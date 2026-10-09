---
title: "RESONAL's Own Setup"
---

This chapter briefly introduces systems that aren't in the public version of the workflow but that I've added in RESONAL's real environment. The public version is a simpler version with these removed.

## Choosing how the music video (MV) looks is even stricter

At RESONAL, when I start the MV for a new song, the AI first writes a selection table that rates all 13 styles one by one, and only then decides which style to use. If it picks the same style as a recent song, it writes down why. That's because sliding back to the same style out of habit happens a lot. It also writes out all 18 axes, without skipping even the ones left at their defaults.

## Check items and a nightly audit

In the RESONAL environment, there are 31 check items from planning to release. When finishing a song, I keep polishing until all of them pass.

After an MV is rendered, the AI makes a sheet of frames taken from fixed points and looks at it to make sure nothing is wrong.

![Contact sheet for Heat Shock. 24 frames taken at even intervals across the whole song, laid out side by side](/images/resonal-pipeline/selfcheck-heat-shock.jpg)
*Contact sheet for Heat Shock. 24 frames taken at even intervals across the whole song, laid out side by side*

After release, every night at 8 p.m., the system compares what's live on YouTube with my local records. I get a Slack notice only when there's a problem. For example, once a video from before mastering went live as the main video, so I added a check to this audit to catch that.

## "It ran" and "it did what I meant" are different things

While handing off long automated jobs, there were several times when a job ran to the end with no errors, but the result wasn't what I meant. For example, a job that adds a link to the main video on each short recorded that it had "added" the link when it actually hadn't.

So now I don't count a job as a success just because it reports "done." I check the result itself before calling it complete. This idea is also in the public version's instructions for the AI.

## How I make MVs these days (as of October 2026)

Since Claude Opus 5.5 came out, I've found it very strong at motion graphics and 3D modeling. So my recent MVs include experiments with these kinds of visuals.

I still use the overall flow of the workflow as before. For the MV part, though, rather than following the public version's axes and looks, I'm exploring new visuals by going back and forth with Claude directly.

For example, for Dive Reflex, I had Claude build a 3D body of water. I moved a camera across the surface and underwater, filmed scenes, and used them in the video.

https://www.youtube.com/watch?v=IjU-iixxmxU

Recently, I also made a video that mixes 3D with watercolor-style 2D. The song and MV will be released soon.

https://x.com/apopotoapoto/status/2106767076514034148

## Summary

In the RESONAL environment, on top of the public version, I use a stricter way to choose how the MV looks, plus check items and a nightly audit. For recent MVs, I'm also trying new visuals such as 3D by working with Claude directly. I also check "it ran" and "it did what I meant" separately.
