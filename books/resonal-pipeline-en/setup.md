---
title: "A. Setup — Getting Started and Answering Questions"
---

This chapter explains how you start using the public version of the workflow.

## Start by asking Claude Code

To get started, open Claude Code and ask like this. How to ask when you use another AI agent is in the [Introduction](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/start-here#using-an-agent-other-than-claude-code) chapter.

```text
https://github.com/apoto/resonal-workflow
I want to make songs with AI using the workflow at this link.
Please bring it onto my computer and start with the setup. Ask me if anything is unclear.
If you can't work with files on my computer, tell me how to get started with Claude Code instead.
```

The AI then brings the repository onto your computer and starts the setup. First it checks whether you have the tools you need. If anything is missing, it shows you how to install it and asks "OK to install?" one at a time. It never installs anything before you agree.

## Answer the questions

Once the tools are ready, the AI asks about the music you want to make, one question at a time. If you don't know an answer, say "decide later" and move on.

| # | What it asks | Example answers |
|---|---|---|
| Q1 | The kind of music you want to make | "Night-city city pop, laid-back" "Piano ballads" |
| Q2 | Theme and world | "Loneliness in the city, and small comforts" "Teenage days after school" |
| Q3 | The singer or character, and the image of the voice | "No character" "A young woman's clear voice" |
| Q4 | The language of the lyrics and any style preferences | "Japanese, with a little English in the chorus" |
| Q5 | The unit name and how credits are written | "MOONLIT LANE" |
| Q6 | Loudness (`streaming` or `loud`) | If unsure, `streaming` |
| Q7 | External services to use | "Suno" "I'll provide my own" "None" |
| Q8 | Where to release | "YouTube only" "No release" |

You can make songs without a character, as voice-only songs. If you have a character illustration, it's used to keep the look consistent across cover images and music videos (MVs). If you have a character, the AI will talk in that character's voice in later conversations.

When you've answered everything, the AI writes the settings files and shows you what's in them. Once you approve, setup is done. From then on, say "I want to make a new song" and it starts with planning.

## You can choose your external services

The workflow uses external services for audio, images, video materials, and notifications. There are recommendations, but you can swap in other services or do things by hand.

![You can choose the services you use](/images/resonal-pipeline/tools.png)
*There are recommendations, but during setup you can swap in whatever you want to use*

| Use | Recommended | Other options |
|---|---|---|
| Audio | Suno | Another service / put in audio you made yourself |
| Images (cover) | codex CLI | Another tool / prepare your own |
| Video materials (MV backgrounds) | Kling MCP | Another tool / none (still-image backgrounds) |
| Notifications (receive the finished MV) | Slack | None |

For every service, generation only happens after you check, and if it fails, the AI won't remake anything on its own. Prices and terms differ by service and can change. Before you use one, check its pricing page and terms.

## Works for any genre

The public version doesn't include RESONAL's genre or 彩瀬??'s settings. Planning, lyrics, and composing all work from the answers you gave during setup, so you can make a ballad or an anime song with the same flow. As a filled-in example, `profile.example/` contains the settings for a fictional unit that makes night-city city pop.

You can change the settings later. Ask something like "I want to redo the setup" or "I want to use a different service for image generation," and the AI will ask again about just that item.

## Want to know more? Ask the AI

To learn what's in the settings files, or the details of connecting external services, ask the AI.

```
Explain each file that was written during setup
I want to use my own tool for image generation. How should I set it up?
```

## Summary

The public workflow starts when you give Claude Code the repository URL and ask it to do the setup. The AI asks one question at a time and writes settings files from your answers. It shows recommended external services, but you can swap in other services or do things by hand.
