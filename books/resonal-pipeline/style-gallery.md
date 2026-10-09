---
title: "B-5 補足. スタイル図鑑 — MVの見せ方の見本"
---

この章では、公開版のリポジトリに入っているミュージックビデオ（MV）の見せ方を、画像で一覧します。最初に既定の型、続けて `styles/` の13のスタイルを並べます。画像は、RESONALの公開済みのMVから4コマずつ切り出したものです。画像の下のリンクから、実際に動いているMVをYouTubeで見られます。キャラクターや背景の絵は曲ごとに差し替えるので、自分の曲では配色も絵も変わります。

MVの工程で「MVの見せ方を選びたい」と伝えると、AIが曲の雰囲気と歌詞から候補を挙げます。どのスタイルも、そのまま使うことも、作り変えることもできます。

## spectrum-still（既定の型）— 1枚絵×カメラ割×七色の光

![](/images/resonal-pipeline/style-spectrum-still.jpg)
*RESONAL「Killframe」 — [YouTubeでMVを見る](https://youtu.be/bkfLe8vvxvo)*

静止画1枚をカメラ割で見せ、被写体の後ろに七色の光、サビ前に光のトンネル、拍に合わせて弾む字幕を重ねます。`tools/make_mv.sh` がそのまま作るのはこの型です。向くのは、明るく疾走感があり、サビの盛り上がりがはっきりした曲です。

## scatter-mincho — 散らし明朝＋デジタル崩壊

![](/images/resonal-pipeline/style-scatter-mincho.jpg)
*RESONAL「Skip Intro」 — [YouTubeでMVを見る](https://youtu.be/DrbROsdTVws)*

白い極太の明朝を、画面の中央を避けて散らして置きます。色ずれと横に流れる残像、打点で走る砂嵐のノイズが特徴です。向くのは、暗く攻撃的で速い曲です。

## ring-visualizer — ネオンの円形ビジュアライザ（歌詞なし）

![](/images/resonal-pipeline/style-ring-visualizer.jpg)
*公開版の実装で書き出した見本（素材はRESONAL「Frequency」のカバーと音源）*

被写体を中央に置き、音に反応するネオンの円形の波形が周りでうねります。歌詞は出しません。向くのは、歌詞より音を聴かせたい曲やインストです。RESONALの公開曲では使っていないので、この画像だけは見本として書き出しました。

## white-cut — 白地×中央の黒明朝×ハードカット

![](/images/resonal-pipeline/style-white-cut.jpg)
*RESONAL「Heat Shock」 — [YouTubeでMVを見る](https://youtu.be/LqBNN80fqk4)*

白い背景の真ん中に、黒の明朝を縦書きで置きます。拍でハードカットし、行と行のあいだに何も出さない「間」を作ります。向くのは、静かで洗練された、切ないミドルテンポの曲です。

## photocopy-zine — ジン／コラージュ・パンク

![](/images/resonal-pipeline/style-photocopy-zine.jpg)
*RESONAL「Repeat Offender」 — [YouTubeでMVを見る](https://youtu.be/5KChsASUCpI)*

コピー機のザラつきと網点、生成りと黒に赤ピンクを差した配色、切り貼りしたような文字です。向くのは、明るいのに毒があって、速い曲です。

## pink-bounce — ピンク高キー×丸文字×デコ盛り

![](/images/resonal-pipeline/style-pink-bounce.jpg)
*RESONAL「おかわりアポカリプス」 — [YouTubeでMVを見る](https://youtu.be/-ykcryweTcE)*

ピンク基調の明るい画面に、2重のフチの丸い極太文字が1文字ずつ弾んで出ます。ハートや星のデコを盛ります。向くのは、明るくかわいい曲です。

## crimson-gothic — 黒×赤の退廃ゴシック

![](/images/resonal-pipeline/style-crimson-gothic.jpg)
*RESONAL「Cold Read」 — [YouTubeでMVを見る](https://youtu.be/Ly2ydNliDqo)*

黒と赤を基調に、和文は明朝、英字はセリフ体で出します。端の縦書き・中央の巨大な1文字・1文字ずつ積む出し方を、ハードカットで切り替えます。向くのは、暗く妖艶で不穏な曲です。

## shape-burst — 跳ねて出る文字×図形のバースト

![](/images/resonal-pipeline/style-shape-burst.jpg)
*RESONAL「House Arrest」 — [YouTubeでMVを見る](https://youtu.be/1KtxaZI0MoM)*

極太のゴシックが1文字ずつ下から跳ねて出て、1文字ごとに図形（□○△◇✕）がはじけます。向くのは、クールで挑発的な、ノリの強い曲です。配色を変えれば明るい曲にも使えます。

## invert-shapes — 白いソリッド図形×ネガポジ反転

![](/images/resonal-pipeline/style-invert-shapes.jpg)
*RESONAL「Static Hazard」 — [YouTubeでMVを見る](https://youtu.be/Zeq87GAhX7Y)*

真っ白な図形の上に極太の角ゴシックを置き、図形に重なった部分だけ文字を黒に反転させます。色は暗い紫・白・黒の3色だけです。向くのは、暗く攻撃的な曲です。

## sky-keyvisual — 1枚のキービジュアル×モーショングラフィックス

![](/images/resonal-pipeline/style-sky-keyvisual.jpg)
*RESONAL「Extra Time」 — [YouTubeでMVを見る](https://youtu.be/2xJ9oBm7euM)*

背景・中央のキャラ・白い線のグラフィックの3層で作り、展開の変わり目でグラフィックの密度と配置を切り替えます。キメでキャラを黒いシルエットにすることもあります。向くのは、明るく爽快で疾走感のある曲です。

## burn-in — 黒地×補色の残像

![](/images/resonal-pipeline/style-burn-in.jpg)
*RESONAL「Afterimage」 — [YouTubeでMVを見る](https://youtu.be/ioRQtF5NO4E)*

真っ黒な背景の中央に白い文字を出し、消えた歌詞がシアンとマゼンタの残像として同じ場所に焼き残ります。向くのは、切なく壮大で、静かな所と盛り上がりの差が大きい曲です。

## lowpoly-corridor — ローポリの3D世界×動くカメラ×立つキャラ

![](/images/resonal-pipeline/style-lowpoly-corridor.jpg)
*RESONAL「Poppy Requiem」 — [YouTubeでMVを見る](https://youtu.be/9u6BlEb3n5E)*

ローポリの3Dの世界を仮想のカメラが駆け抜け、透過したキャラを3D空間に立たせます。向くのは、壮大で暗く荘厳な曲です。

## plate-swap — 面の切り替え×静止画×刷り出す文字

![](/images/resonal-pipeline/style-plate-swap.jpg)
*RESONAL「Rerun Season」 — [YouTubeでMVを見る](https://youtu.be/_jEE-ct5L8Y)*

数種類の背景を小節の頭で丸ごと切り替え、キャラは静止画の差し替えで見せます。極太のゴシックが一瞬で刷り出され、しばらく残って1フレームで消えます。向くのは、夜っぽくクールな、中〜速テンポの曲です。

## portrait-frame — 静止した立ち絵×切り替わる背景×縦書きの積み上げ

![](/images/resonal-pipeline/style-portrait-frame.jpg)
*RESONAL「Whiteout」 — [YouTubeでMVを見る](https://youtu.be/yUfSKgwiono)*

立ち絵は動かさず、背景だけが短い動画で切り替わります。縦書きの明朝の歌詞が右から左へ積み上がり、まとめて消えます。向くのは、静かで壮大な、叙情的な曲です。

## まとめ

公開版には、既定の型と13のスタイルが入っています。どれも、曲の配色や絵を差し替えて使います。気に入ったものはそのまま使い、物足りなければ[「B-5. ミュージックビデオ（MV）」](https://zenn.dev/apoto/books/resonal-pipeline/viewer/music-video)の章のとおり、同じ型で作り変えたり新しく足したりできます。
