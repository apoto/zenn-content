---
title: "B-3. Composing — Text for Suno, and the Cover Image"
---

This chapter explains the composing step. The AI prepares the text you paste into the music generator and a cover image. You generate the audio with Suno or a similar service and put it in place. Composing is the second of the places where you make the call.

## Flow

1. The AI prepares three pieces of text to paste into Suno
2. The AI makes a cover image
3. You generate audio in Suno and put in the one you like
4. The AI checks the audio and moves on to mastering

Suno is recommended, but in the setup settings you can swap it for another service or for audio you made yourself. Whichever you choose, you generate and download the audio by hand.

## Three pieces of text for Suno

The AI writes three text files into the song's folder. You just open them and paste them into Suno's input fields.

| File | Field to paste into | Contents |
|---|---|---|
| `suno_lyrics.txt` | Lyrics | The Suno version of the lyrics, written in the lyrics step |
| `suno_style.txt` | Style of Music | Genre, tempo, vocals, and how the song develops, written in English |
| `suno_exclude.txt` | Exclude Styles | Sounds and singing styles you don't want |

The AI tells you exactly what to paste into which field, then stops. Suno's title field sometimes still holds the value from the previous song, so check it every time.

## Making the cover image

Along with the text, the AI makes a cover image. It's a wide image, and it becomes the base for the music video (MV) background, the thumbnail, and the cover art. The image has no text in it. The song title is added later.

If there is a character, I have the AI draw it with specific instructions for the facial expression and pose. This started at RESONAL when I looked at a generated image and said, "This expression feels like ChatGPT, kind of AI-ish. Giving it a stronger expression would probably make it feel less AI." (この表情、ChatGPTって感じというかAIっぽい。もっと表情を作った方がAIぽさがなくなりそう)

Image generation can cost money or have usage limits. Even if it fails, the AI won't remake it on its own. It asks you whether to try again.

## You make the audio and put it in place

Generate a few takes in Suno, listen and compare, download the one you like as a WAV, and put it in the song's folder as `audio.wav`. When it's there, tell the AI "it's in". If none of them feel right, tell the AI what bothered you, and it will revise the text and hand it to you again.

```
I want the voice to be brighter
The chorus doesn't build up enough
Slow the tempo down a little
```

## Don't edit the length of the generated audio

In this workflow, you don't edit the length of the generated audio. Even if the instrumental intro or outro is long, it isn't cut, and the final fade-out isn't trimmed either. The generated music itself is treated as the finished work.

If you don't like the length, you regenerate instead of cutting. With RESONAL's Stutter Step, I said "the outro is too long" and regenerated, but the outro didn't go away. So I asked for more lyrics and regenerated with more sung parts. It seems that when the sung part is short, the length tends to get filled with instrumental parts.

## If you want your own vocals or instruments

If you want to sing yourself, or use your own guitar sound, just tell the AI. Make an instrumental backing track without vocals in Suno and put it in with your own recording, and the AI will line up the timing and volume and combine them into one track. If you care about the texture of the sound, mix it in a DAW and put that as `audio.wav`, and you can go straight to the next step.

## Want to know more? Ask the AI

For how the Suno text is written or how the image is made, try asking the AI.

```
Explain what you wrote in suno_style.txt, and why
I want to prepare the cover image myself. Where should I put it?
```

## Summary

In composing, the AI prepares three pieces of text for Suno and a cover image, and you generate the audio in Suno and put it in place as `audio.wav`. The length of the generated audio isn't edited. If you don't like it, regenerate. You can also add your own vocals or instruments.
