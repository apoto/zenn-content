---
title: "Introduction — Please Read This First"
---

This book is a manual for a workflow (a written set of steps) for making a song and its MV from start to finish, just by talking with AI. You don't need to read it all from the start. Read this chapter, paste the prompt from [Getting Started](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/start-here#getting-started) into the AI, and you can do the rest by talking with the AI.

日本語版は[こちら](https://zenn.dev/apoto/books/resonal-pipeline)。

The workflow is based on how the AI music unit **RESONAL** makes its songs. The workflow itself is public on GitHub.

@[card](https://github.com/apoto/resonal-workflow)

## What you can do with this book

- Finish a whole song, from planning, lyrics and composing to finishing the sound (mastering), the music video (MV) and release prep, just by talking with AI
- Remake the look of your MV the way you like, just by describing it in words
- Start with about $30 a month in subscriptions (your MV gets finished even without video generation AI)

The AI does most of the work. Your part is the decisions and the finishing touches: choosing ideas, making the audio, approving the MV, and publishing it on YouTube and other places.

## What you'll learn

- How to split the work between what you leave to AI and what people decide
- How to tell the AI what to fix when things don't turn out the way you imagined

There's also a two-minute video that walks through the whole flow (in Japanese).

https://x.com/apopotoapoto/status/2108705141176345003

## What this book doesn't cover

- Music theory, or detailed techniques for writing lyrics and composing
- How to use a DAW or video editing software
- Detailed instructions for each service, such as Suno or Kling
- How to distribute or monetize your music

## Who this is for

Maybe you're interested in making songs and MVs with AI, but you don't know how, or you can't get to the finish line, for reasons like these. If so, I'd love for you to try it.

- You've never made music or video: you can first experience a finished song and MV made by AI, on your own computer
- You can only do one of music or video: swap in your own work for the part you're good at, and let the AI handle the other, so you can finish pieces efficiently
- You can't give the AI good instructions: the AI asks you questions as it goes, so you only pick from the ideas it shows and say what bothers you in your own words
- The popular methods cost too much: you can make an MV mainly from images, without using a video generation service

## How to read this book

I assume you've already used AI tools like Claude or ChatGPT. You don't need any special knowledge of music or video production.

This book covers only the minimum you need to know to use the workflow. I've left out detailed explanations of how things work and of technical terms. If you're curious, ask the AI. It will read the repository and answer. Each chapter stands on its own, so start wherever you like.

| What you want to know | Chapter |
|---|---|
| I just want to get started | Keep reading this Introduction chapter |
| About RESONAL and the author | [What Is RESONAL](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/what-is-resonal) |
| The overall flow | [Overview](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/overview) |
| What you'll be asked during setup, and how to choose services | [A. Setup](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/setup) |
| What happens in each step | The chapters from [B-1. Planning](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/planning) to [B-6. Release Prep](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/release-prep) |
| Examples of MV looks | [B-5 Supplement. Style Gallery](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/style-gallery) |
| What you do, and the thinking behind this workflow | [The Human's Job](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/my-role) |
| The environment RESONAL actually uses | [RESONAL's Own Setup](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/resonal) |

:::message
This book and the public workflow are "v1" as of October 2026.
:::

## What you need

### Required

- A Mac computer (I haven't tested it on Windows)
    - Apple silicon (M1 or later) is recommended. On older Macs, timing the lyrics and rendering the MV take much longer. Plan for about 10 GB of free disk space.
- A [Claude](https://claude.ai/) or [ChatGPT](https://chatgpt.com/) account
    - You'll use Claude Code or Codex, which can work with the files on your computer. I've tested both.
    - If you use Codex, also read [Using it with Codex](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/start-here#using-it-with-codex).
- A way to make audio
    - I recommend [Suno](https://suno.com). You can also use other services, or audio you made yourself.

A normal chat in your browser can't handle the files on your computer, so this workflow won't run there.

### Nice to have

| What | Recommended service | What it does | Without it |
|---|---|---|---|
| Image generation tool | Codex CLI | The AI makes the cover image and image materials for the MV | Use images you prepared yourself |
| Video generation tool | Kling MCP | The AI makes video materials for the MV | Make the MV mainly from images |
| Notification tool | Slack | Get the finished MV on your phone | Check it on your computer |

During setup, the AI asks which tools you have and which services you want to use, and you choose. For details, see the [A. Setup](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/setup#you-can-choose-your-external-services) chapter.

For any other tools you need, the AI checks after you start and shows you how to install anything missing (it asks before installing).

## Using it safely

This workflow runs on your own computer. How you use it, the songs you make, and the information you enter are never sent to me (apoto), the author.

It only talks to the outside world when it asks a service you chose to do something. Suno and image or video generation services receive descriptions of what you want to make and any reference images. If you use Slack, it receives the finished MV. Your conversations with the AI (Claude Code and so on) are handled under each service's terms.

The following important information is saved on your computer.

- The token for connecting to Slack, if you use Slack (`.env`)
- Settings such as the names you gave during setup (`profile/` and `workflow.config.json`)

These are set up from the start so they won't be uploaded to GitHub or anywhere else. Please be careful when you have the AI search the web or look things up with another tool. Make sure your token and personal information don't end up in search queries or in outside tools. Don't paste your token into the chat. Write it directly in `.env`.

## Getting started

Open Claude Code or Codex, copy the text below as is, paste it, and send it.

```
https://github.com/apoto/resonal-workflow
I want to make songs with AI using the workflow at this link.
Please bring it onto my computer and start with the setup. Ask me if anything is unclear.
If you can't work with files on my computer, tell me how to get started with Claude Code or Codex instead.
```

The link at the top is where this workflow lives. The AI reads the link, brings what it needs onto your computer, and starts the setup.

During setup, the AI asks you one question at a time: the mood of the music you want to make, the theme, the singer, what matters to you in the lyrics, the unit name, the loudness, the services to use, and where to publish. If you don't know an answer, say "decide later" and you can move on.

For reference, I run Claude Code inside VS Code to work, and when I'm out, I check things and give instructions from the Claude app on my phone.

### Using it with Codex

I've confirmed that it works with Codex too, from setup to rendering the MV. One thing: MV rendering stops inside Codex's safety sandbox, because the rendering tool launches a browser. If rendering stops, ask Codex to run it outside the sandbox (approve it if Codex asks for permission).

### Using another AI agent

I've tested it with Claude Code and Codex. If you use another agent, first ask it to reshape the workflow into a form that's easy for it to use, and then start.

```
https://github.com/apoto/resonal-workflow
I want to make songs with AI using the workflow at this link.
This workflow is written for Claude Code and Codex. After you bring it onto my computer, first reshape it into a form that's easy for you to use, and then start the setup. Ask me if anything is unclear.
If you can't work with files on my computer, tell me how to get started with Claude Code or Codex instead.
```

## Making a song

When setup is done, say this.

```
I want to make a new song
```

The AI then works through the steps in order. When it reaches a point where you need to decide, it stops and tells you what it needs from you.

| Where you decide | What you do |
|---|---|
| Planning | Pick one of the 2–3 ideas the AI gives you |
| Composing | Paste the text the AI prepared into Suno or a similar service to generate the song, and give the AI the audio you like |
| MV | Watch the finished video and say whether it's OK or what you'd like changed |
| Publishing | Publish to YouTube and other places, using the images and descriptions the AI prepared |

## What to say when you're stuck

| When | What to say |
|---|---|
| You want to know how far you've gotten | "How far along are we?" |
| You want to continue from last time | "Continue this song" |
| You want to change settings (the character, the mood of the music, etc.) | "I want to redo the setup" |
| You want to add your own singing or instruments | "I want to sing the vocals myself" |

## It's free

This book is free. If you found it useful, supporting it with a badge would really encourage me.
