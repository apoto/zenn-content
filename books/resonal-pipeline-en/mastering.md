---
title: "B-4. Mastering — Getting the Volume Ready for Streaming"
---

This chapter explains the step that turns the generated audio into the finished audio used for streaming and the music video (MV).

## What is mastering?

Mastering is the step that adjusts the volume and tone of a finished song so it's ready for release. In the public version, it makes one finished `<Title>.wav` from the audio you generated with Suno or a similar service (`audio.wav`). The AI does the work with a script, so you don't need any audio knowledge.

## The only thing you choose is how loud it is

You decide just one thing: the "loudness and tone" question asked during setup.

| Option | Good for |
|---|---|
| `streaming` (default) | Most songs. Matches the standard volume of streaming services and keeps the original tone as is |
| `loud` | Songs where you want punch and flash, like EDM or rhythm-game music |

If you're unsure, choose `streaming`. You can change it later by saying "I want to redo the setup".

## What the AI does

The AI runs `mastering/auto_master.py` to bring the volume to the target. It measures the result in numbers and gives a pass or fail, and only makes `<Title>.wav` when it passes. It doesn't change the length of the audio. It doesn't cut the intro, the outro, or the final fade-out either.

It shows you the results in a table, with the meaning of each number.

## If something bothers you, say it in words

Listen, and if something bothers you, say it the way you feel it. The AI turns that into adjustments and makes it again.

```
It sounds muffled
The high end is harsh
There's not enough bass
```

You can also put in audio you mastered yourself in a DAW or similar tool as `<Title>.wav`. Automatic mastering is for finishing quickly. For songs where you care about the finish, doing it by hand can give a better result.

## Want to know more? Ask the AI

For terms like LUFS, or what the script does inside, try asking the AI. It will read the repository and answer.

```
Explain the numbers in the mastering report, for a beginner
Tell me a bit more about the difference between streaming and loud
Explain what auto_master.py does, step by step
```

## Summary

In mastering, the only thing you choose is `streaming` or `loud` during setup. The AI adjusts the volume, checks it in numbers, and makes the finished `<Title>.wav` when it passes. If something bothers you, say it in words.
