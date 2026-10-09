---
title: "Overview — A. Setup and B. Making a Song (6 Steps)"
---

This chapter gives the big picture of making one song with the public version of the workflow (resonal-workflow).

## Two stages

The workflow has two main stages.

- A. Setup: you do this only once, right after you put the repository on your computer. The AI asks about the music and the singer you want, and writes your answers into settings files
- B. Making a Song: starts every time you say "I want to make a new song." You and the AI take turns through 6 steps, from planning to release prep

From your second song on, you can start by saying "I want to make a new song."

![A. Setup and the 6 steps of B. Making a Song](/images/resonal-pipeline/overview.png)
*A. Setup and the 6 steps of B. Making a Song*

## The 6 steps of B. Making a Song

| # | Step | What the AI does | What you do |
|---|---|---|---|
| B-1 | Planning | Offers 2–3 song ideas | **Pick an idea** |
| B-2 | Lyrics | Writes and revises the lyrics | (You can read them and ask for changes) |
| B-3 | Composing | Prepares the text to paste into the audio generator, and a cover image | **Generate the audio in Suno or a similar service and put it in place** |
| B-4 | Mastering | Adjusts the loudness for streaming | (You can say what bothers you) |
| B-5 | Music Video (MV) | Makes a music video with on-screen lyrics | **Watch it and say whether it's OK or what to change** |
| B-6 | Release Prep | Gathers what you need to publish, like the description and cover art | **Upload it** |

## You decide in four places

The workflow stops and waits for your decision at the 4 points in bold in the table.

1. Pick an idea: choose one of the AI's song ideas. If you want to mix ideas or change something, say so too
2. Make the audio: paste the text the AI prepared into Suno or a similar service, generate, and put the one you like in place
3. Watch the MV: approve it, or say what you'd like changed. You can ask for changes as many times as you want
4. Upload: upload to YouTube and other places, following the checklist

At these 4 points, the AI tells you exactly what it needs from you and then stops.

That said, the AI works a little differently each time, so it may ask "Is this OK?" at other points too. For example, it may ask you to check the lyrics once it has written them. When that happens, just answer. At any step, if something bothers you, tell the AI and it will fix it.

## You can stop and pick up where you left off

It's fine if one song takes several days. The AI figures out the next step from what's in the song's folder, so you don't need to remember the order. To pick up again, say something like this.

```
How far along are we?
Continue this song
```

The results, such as the plan, lyrics, audio, and MV, collect in a folder for each song (`songs/<date>_<song title>/`).

## Want to know more? Ask the AI

To learn how the steps are run, or what's in each file, ask the AI.

```
Tell me what ./next.sh does
Explain each file in the song's folder
```

## Summary

The public workflow is made of a one-time setup and 6 steps: planning, lyrics, composing, mastering, MV, and release prep. You decide at 4 points: picking an idea, making the audio, watching the MV, and uploading. If you stop partway, just ask the AI and you can pick up where you left off.
