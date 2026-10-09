---
title: "The Human's Job — Deciding and Putting It into Words"
---

This chapter explains what people do while the AI and scripts move the steps forward. First, let me describe the thinking behind this workflow.

## The thinking behind this workflow

In this workflow, the AI makes the first draft automatically. But to brush it up into something better, a person has to check, decide, and give direction. I built it that way on purpose.

I see making things with today's AI as an extension of human creativity. The AI is a tool that does the hands-on work. Deciding what to make and what to fix is up to people. The system in this book is not meant to reduce the number of people involved. It is meant to let people focus on decisions.

As AI keeps improving, maybe someday even human decisions won't be needed. But at least for now, this is how I build my workflow.

## You decide in four places

In the public version of the workflow, there are four places where you make decisions.

| # | Step | What you do |
|---|---|---|
| 1 | Planning | Pick one of the 2–3 ideas the AI suggests |
| 2 | Composing | Generate audio with Suno or a similar service, and put the WAV of the take you like in the song folder |
| 3 | Music Video (MV) | Watch the main video and the short, then approve them or say what you want fixed |
| 4 | Release Prep | Upload to YouTube and streaming services |

At these four places, the AI stops and tells you clearly what it needs from you. I've told the AI, "Don't decide on behalf of the human."

The AI gets everything it can ready before it stops, so what you need to choose or watch is already in front of you.

For me, step 1 (planning) and step 2 (composing) are usually decided in one go. Step 3, the MV, takes several rounds. I say what I want fixed, the AI remakes it, and I watch it again.

## Give what you want fixed a name

When I ask for fixes to an MV, I try to be specific about what I want changed.

For example, in the review for Okawari Apocalypse, I sent back these three points:

- At 2:44 the lyric is "gochisousama" (thanks for the meal), so I want to switch to a scene where she's full (2:44で「ごちそうさま」と歌うので、満腹のシーンに切り替えたい)
- 彩瀬??'s expression in the scene at 0:12 looks AI-like. It seems like it needs more expression (0:12のシーンの彩瀬??の表情が、AIっぽい。もっと表情を作ったほうがよさそう)
- At 0:05, I want the camera to swing so 彩瀬??'s face is in close-up. The idea is to add movement to the picture during the intro (0:05でカメラを振って、彩瀬??の顔がアップになるようにしたい。イントロ中に映像に動きをつけたい意図)

When **the time, what you want, and why** are all there, like in the first and third points, the AI fixes it in one try.

The second point, "It seems like it needs more expression," was hard to fix as written. That time, 彩瀬?? broke down what an "AI-like expression" actually is and put it into words as three things: **symmetry, no emotional symbols, and a safe, bland smile**. So I asked for the opposite (close one eye to make it asymmetric, angle the eyebrows, add symbols like sweat drops and sparkles), and the expression started to act.

With only "make it better" or "more expression," the AI doesn't know what to change. So I think the human's job in a review is to pin down what's missing, give it a name, and say it. The public version's `CLAUDE.md` also tells the AI that when an instruction is vague, it should list exactly what information is missing and ask, instead of guessing what "make it better" means.

## Learn the basics, and learn from existing work

To name what's missing, you need to know the basics of the field. If you don't know music genres, mastering terms, or the names of camera moves, you can't point to what's missing.

I'm learning the basics little by little, by reading the prompts the AI wrote for songs and asking 彩瀬?? what mastering numbers mean. I can look at what was generated and ask, "How does this part work?" or "Why did you do it this way?" That makes learning easier than it used to be.

When I make Skills for lyrics or video, I also draw on the styles of existing works and on ways of thinking about lyric writing and video editing. I learn from existing works and techniques "why it feels good," and turn that into words the AI can follow. For example, I make one-line rules like "drop one word everyone would pick" and "don't explain feelings, describe them" for lyrics, and "at the start of a section, show the place in a wide shot, then the person, then a close-up" for video.

It's the same when I find an MV I like. I put that scene into words in three steps: "what is happening," "why it feels good," and "how I'd use it in my own song." What I borrow is the thinking and the technique. I never use the lyrics or footage as they are.

## How I work on RESONAL

For RESONAL, I usually don't sit at a computer. I work from my phone. I get videos and text from the AI in a Slack thread for each song, and I reply with instructions from the Claude phone app. In August 2026, I also built a dedicated review app that let me drop a pin on a specific moment in a video and send a fix, but I don't use it now. The Claude app and Slack are enough for now, and the accuracy of lyric timing, which was the original problem, has gotten much better.

![The review app's feedback screen. You drop a pin on a moment in the video and send a fix with a frame image](/images/resonal-pipeline/studio-feedback.jpg =360x)
*The review app's feedback screen. You drop a pin on a moment in the video and send a fix with a frame image*

## Summary

In the public version, you make decisions in four places: choosing an idea, generating and placing the audio, watching the MV, and uploading. In MV reviews, I give the time, what I want, and why, and I name what's missing. To do that, I learn the basics and the thinking behind existing works, and turn them into my own words as instructions for the AI.
