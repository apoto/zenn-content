---
title: "FAQ"
---

Here are things you might wonder about before you start, or while you're using it. If your question isn't here, feel free to ask the AI.

## Q. The song or MV isn't coming out the way I imagined

Don't worry if it isn't right the first time. I also fix things little by little every time, going back and forth with the AI. Even at RESONAL, I finish each MV after about 5 to 20 rounds.

Try working it out together with the AI. If you say "this part bothers me," the AI will fix it. If you can't put it into words, ask the AI, "What could I change to make it better?"

## Q. Is this workflow finished?

No. It's the workflow I'm still experimenting with, published as it is right now.

I hope each person who uses it will make it better in their own way. You can customize it from this base, or fold it into your own know-how, AI agents, harnesses, or workflows. It's under the MIT license, so feel free to use it.

I'd be happy if it helps you in some way.

## Q. How much does it cost?

The workflow itself is free. What costs money is the monthly fee of the services you use with it. Rough prices as of October 2026:

| What | Monthly (approx.) |
|---|---|
| Claude Pro or ChatGPT Plus (one of them; for Claude Code or Codex) | about $20 |
| Suno (Pro, commercial use allowed) | about $10 |
| (Optional) video generation: Kling | from about $10 |

With only the required services, you can start at about $30 a month. If you choose ChatGPT Plus, cover image generation (Codex) is included. If you choose Claude Pro, prepare images yourself or add ChatGPT Plus.

If you try to make an MV with video generation AI alone, even a 3-minute song needs dozens of 5-second clips, and with retakes your credits run out quickly. In this workflow, MVs are built mainly from images, so you can finish one without video generation.

Prices can change, so it's a good idea to check each service's pricing page before you start.

## Q. Can I release or make money from the songs I make?

It depends on the rules of the services you used. With audio generation services, whether you can use the results commercially may depend on your plan. Check the latest rules before you publish. Credits and AI disclosure are covered in the ["B-6. Release Prep"](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/release-prep#check-the-rules-for-credits-and-ai-disclosure) chapter.

## Q. Can I use it with ChatGPT (Codex)?

Yes. I've confirmed that it works with Codex too, from setup to rendering the MV. Only MV rendering needs to run outside Codex's safety sandbox. Details are in the ["Introduction"](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/start-here#using-it-with-codex) chapter.

## Q. How do I stop using it?

Ask the AI "Clean up what this workflow installed". To delete things yourself, remove the folder you cloned, the dedicated boxes (`~/.venvs/resonal-workflow` and `~/.venvs/rembg`), and the models (`~/.cache/whisper` and `~/.u2net`). Tools such as whisper go into a dedicated box rather than your whole computer, so other tools are not affected.

## Q. I got an error, or it stopped partway

No need to panic. Show the error message to the AI as is and ask, "Fix this." If you lose track of where you are, ask, "Where are we now?" and it will tell you what comes next.

## Q. Can I use it without knowing about music or video?

Yes. If you see a word you don't know, ask the AI, "What is ___?"

## Q. Can I make songs with my own character?

Yes. During setup, describe your character and the kind of singing voice you imagine. If you have a character illustration, it's used to keep the cover image and the MV's look consistent. You can also make songs without a character.

## Q. Something doesn't work or I don't understand something. Where can I send feedback?

Feel free to reach out on X ([@apopotoapoto](https://x.com/apopotoapoto)). Things that don't work, parts that are hard to understand, and requests like "I wish it did this" are all welcome.
