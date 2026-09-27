---
title: "MV② 歌詞同期 — LYRICS.md と Whisper の秒を合わせる"
---

この章では、歌詞を画面に出すタイミングを決める `06_build_lyrics.py` について説明します。第9章で取った Whisper の秒と、歌詞の正本 `LYRICS.md` を組み合わせて、Remotion が読む `lyrics.json` を作るスクリプトです。

例として、Cotton Overkill のプロジェクトに入っている `06_build_lyrics.py` を使います。

## 語は LYRICS.md から、秒は Whisper から取る

`06_build_lyrics.py` では、画面に出す語と、それを出す秒を、別々のところから取っています。

![Stutter Step のサビ。Whisper が語ごとの秒を測り、「タ・タ・タップ」も0.16秒刻みで分かれる](/images/resonal-pipeline/whisper-timing.jpg)
*Stutter Step のサビ。Whisper が語ごとの秒を測り、「タ・タ・タップ」も0.16秒刻みで分かれる*

| 取るもの | 取り出し元 | 理由 |
|---|---|---|
| 語（歌詞の文字） | `LYRICS.md` | Whisper の認識結果には空耳が混じるため |
| 秒（出すタイミング） | Whisper の出力 | 実際に歌われた秒を測れるため |

Whisper の認識語を使わないのは、歌を文字起こしすると、聞き間違いが多く出るためです。Cotton Overkill では、「詰めが甘い」が「爪が甘い」に、「ふわっ ふわっ どんっ で」が「ふわふわ飛んで」になっていました。

そのため、語は `LYRICS.md` から AI が表に写し、秒だけを Whisper の結果に合わせます。表は次のような形です。

```python:projects/cotton-overkill-ricochet-mv/tools/06_build_lyrics.py
    # ---- Chorus 1 ----
    (43.76, 1.50, "Cotton Overkill", "de"),
    (45.26, 1.82, "痛くないでしょ？", "d"),
    (47.08, 1.35, "Cotton Overkill", "de"),
    (48.43, 1.53, "でも 立てないでしょ？", "d"),
    (49.96, 1.40, "ふわっ ふわっ", "d"),
    (51.36, 1.52, "どんっ で 終わり", "d"),
```

1行が画面に出る1フレーズで、左から「出す秒」「表示する長さ（hold）」「文字」「フラグ」です。フラグは `d` がサビ（大きく出す）、`c` が静かな区間（控えめに出す）、`e` が英語を表します。Whisper は歌の1まとまり（セグメント）を1つとして秒を返しますが、この曲のサビは「Cotton Overkill」と続きの句を別のカットにしたかったので、1セグメントを2フレーズに割っています。

## 語吸着 — 0.7秒以内の最寄りのオンセットへ

表に書いた秒は、次に Whisper の単語ごとの開始秒（オンセット）に合わせ直します。これを「語吸着」と呼んでいます。

```python:projects/cotton-overkill-ricochet-mv/tools/06_build_lyrics.py
        i = bisect.bisect_left(onsets, t)
        cands = [onsets[j] for j in (i - 1, i, i + 1) if 0 <= j < len(onsets)]
        if not cands:
            continue
        near = min(cands, key=lambda o: abs(o - t))
        if abs(near - t) <= tol and near != t:
            changes.append((t, near, ph["text"]))
            ph["t"] = round(near, 3)
```

各フレーズの秒の前後にあるオンセットを候補にし、最も近いものが 0.7 秒（`tol`）以内にあれば、その秒に置き換えます。0.7 秒より離れているときは、表に書いた秒のままにします。

この処理を足したのは、初めの版ではセグメントの境界の秒だけを使っていて、歌詞がところどころずれていたためです。1セグメントを2フレーズに割った箇所では、割る位置の秒を手で見積もっていました。その見積もりが実際の発声とずれていて、最大で 1.68 秒、0.15 秒を超えるずれが14件ありました。単語ごとの秒に吸着させることで、割った位置も実際に歌われた秒に合うようになりました。

スクリプトを実行すると、0.1 秒を超えて動いたフレーズを、動いた量と一緒に一覧で表示します。

## hold 埋め — 3.5秒を超える間は空ける

次に、各フレーズを表示する長さ（hold）を決め直します。

```python:projects/cotton-overkill-ricochet-mv/tools/06_build_lyrics.py
def refill_holds(phrases: list[dict], max_fill: float = 3.5, end: float = DURATION) -> None:
    """hold を「次のフレーズが出るまで」に伸ばす（ハードカットで間を空けない）。

    間隔が max_fill を超える所＝器楽区間なので、そこは元の hold を保って**画面を空ける**。
    """
    for i, ph in enumerate(phrases):
        nxt = phrases[i + 1]["t"] if i + 1 < len(phrases) else end
        gap = nxt - ph["t"]
        ph["hold"] = round(gap if gap <= max_fill else min(ph["hold"], max_fill), 3)
```

次のフレーズまでの間が 3.5 秒以下なら、次のフレーズが出るまで今のフレーズを表示し続けます。この曲のスタイルは、フレーズをフェードを使わずにパッと切り替える（ハードカット）ので、フレーズとフレーズの間を空けずにつなぐようにしています。

一方で、3.5 秒を超える間は、歌の無い間奏と判断して、元の hold のまま画面を空けます。

## 行の長さからフォントサイズを計算する

歌詞のフォントサイズは、行ごとに自動で計算しています。

```python:projects/cotton-overkill-ricochet-mv/tools/06_build_lyrics.py
def visual_width(text: str) -> float:
    """行の見た目の幅（em単位）。全角=1.0 / 半角=0.55 で概算。"""
    w = 0.0
    for ch in text:
        if ch == " ":
            w += 0.35
            continue
        ea = unicodedata.east_asian_width(ch)
        w += 1.0 if ea in ("W", "F", "A") else 0.55
    return w
```

```python:projects/cotton-overkill-ricochet-mv/tools/06_build_lyrics.py
    boost = 1.0 if is_english else 1.08
    per_em = 0.9 * boost
    safe = 1920 * 0.86
    w = visual_width(text)
    max_size = safe / max(0.5, w * per_em)
    # 見せたい基準サイズ（drop は殴る）
    want = 210 if is_drop else 140
    return int(max(64, min(want, max_size)))
```

行の幅を「1文字の高さ（em）の何倍か」で見積もります。全角は 1.0、半角は 0.55、空白は 0.35 として足し合わせます。そこから、画面の横幅 1920px の 86% に収まる最大のサイズを出し、見せたいサイズ（サビは 210px、それ以外は 140px）と比べて小さいほうを使います。`per_em` の 0.9 と 1.08 は、このスタイルが文字を横に 0.9 倍に縮め、日本語を 1.08 倍に大きくしているのに合わせた値です。

実際の値は次のようになります。

| 行 | 幅（em） | 使われるサイズ |
|---|---|---|
| `Cotton Overkill`（サビ・英語） | 8.05 | 210px（見せたいサイズのまま） |
| `やわらかい？` | 6.0 | 140px（見せたいサイズのまま） |
| `詰めが 甘いのは あんたのほう` | 13.7 | 123px（画面幅に合わせて縮小） |

この計算が必要なのは、画面側の歌詞の部品が折り返しをしない設定になっているためです。長い行を固定のサイズで置くと、行が画面の外にはみ出します。第9章で書いたとおり、番号スクリプトを使わずに `lyrics.json` を作った曲では、この計算が使われず、歌詞が画面外にはみ出したまま本番のレンダーまで進みました。そのため、`lyrics.json` を作る段階でサイズを計算して決めるようにしています。

## 重なりを検査して止める

最後に、前のフレーズの表示が次のフレーズの開始に重なっていないかを検査します。

```python:projects/cotton-overkill-ricochet-mv/tools/06_build_lyrics.py
    for a, b in zip(phrases, phrases[1:]):
        if a["t"] + a["hold"] > b["t"] + 1e-6:
            raise SystemExit(f"[ERR] 重なり: {a['text']!r} > {b['text']!r}")
```

重なりがあると、そこで止まって `lyrics.json` を書き出しません。語吸着や hold 埋めで秒を動かしたあとの状態を、書き出す前に機械で確かめるための検査です。

## Whisper の幻聴に対処する

Whisper は、歌の無い部分や声が聞き取りにくい部分で、実際には無い言葉を返すことがあります。Cotton Overkill では、曲の最後にあるサビの繰り返し（リプライズ）の区間だけを文字起こしし直したところ、Whisper は「ご視聴ありがとうございました!」を返しました。音楽を文字起こしするときに出やすい誤認識です。

この区間は、単語ごとの秒も特定の秒に固まったあと数秒飛ぶ形になっていて、語吸着には使えませんでした。ただ、セグメントの境界の秒だけは返っていたので、その中を他のサビと同じく半分ずつに割ってフレーズを置いています。

```python:projects/cotton-overkill-ricochet-mv/tools/06_build_lyrics.py
REPRISE_FROM = 199.0
REPRISE_SEGMENTS = [(200.06, 207.00), (207.00, 209.44)]
```

199 秒以降のフレーズは語吸着の対象から外し、この2つのセグメントの中に置き直します。この区間だけは機械で決めきれないので、耳での微調整が必要なことを引き継ぎメモに書いています。

## クレジットを小節の頭に置く

RESONAL の MV には、どの曲にも次の3点のクレジットを入れています。文言は固定で、変えません。

```text
AI Vocal 彩瀬??
Produced by apoto
RESONAL
```

既定では、歌い出しの前のイントロで、`RESONAL` → `AI Vocal 彩瀬??` → `Produced by apoto` の順に1枚ずつ、2.5〜3.5秒ずつ出します。切り替える秒は、小節の頭（`60 / BPM * 4` 秒の倍数）に合わせます。勘で秒を置くと、切り替わりが音から浮いて見えるためです。

Cotton Overkill は、0秒から歌が始まる曲でイントロが無かったので、最初の間奏（66.70〜71.96秒）にクレジットを置いています。

```python:projects/cotton-overkill-ricochet-mv/tools/06_build_lyrics.py
    bar0 = math.ceil(66.70 / BAR)
    c1 = bar0 * BAR
    credits = [
        {"text": "RESONAL", "from": round(c1, 3), "to": round(c1 + BAR, 3)},
        {"text": "彩瀬??", "subtitle": "AI Vocal", "from": round(c1 + BAR, 3), "to": round(c1 + BAR * 2, 3)},
        {"text": "apoto", "subtitle": "Produced by", "from": round(c1 + BAR * 2, 3), "to": round(c1 + BAR * 3, 3)},
    ]
    assert credits[-1]["to"] < 71.96
```

この曲は 174 BPM なので、1小節は約 1.379 秒です。間奏が始まる 66.70 秒のあとで最初の小節の頭（約 67.59 秒）から、1小節ずつ3枚を出します。最後の `assert` は、3枚目が歌の再開（71.96秒）より前に終わるかを確かめる検査です。BPM や間奏の秒を変えたときに、クレジットが歌詞に重なるのを防いでいます。

クレジットの文言が入っているかは、レンダーのあとにも `check-mv-credits.sh` でテキストとして検査しています。これは第12章で説明します。

## まとめ

`06_build_lyrics.py` は、語を `LYRICS.md` から、秒を Whisper から取って `lyrics.json` を作ります。秒は単語ごとのオンセットに 0.7 秒以内で吸着させ、表示の長さは次のフレーズまで埋めつつ 3.5 秒を超える間奏は空けます。フォントサイズは行の長さから計算して画面からはみ出さないようにし、重なりがあれば書き出す前に止めます。Whisper が幻聴を返す区間は吸着から外し、クレジットは小節の頭に置いています。次章では、こうして作った `lyrics.json` と `energy.json` を使って、Remotion で画面を組み立てる方法を説明します。
