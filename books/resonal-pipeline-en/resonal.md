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

## What isn't working well yet

- MVs aren't finished in one try: The first video the AI produces often isn't good enough to publish as is. Review rounds run from about 5 for some songs to about 20 for others
- Improvements to the system don't reach songs in progress: When I improve the MV template, it doesn't carry over to songs I've already started
- Some rules only exist as instructions to the AI: There are rules that nothing automatically enforces

## Summary

In the RESONAL environment, on top of the public version, I use a stricter way to choose how the MV looks, plus check items and a nightly audit. I check "it ran" and "it did what I meant" separately, but some things, like the number of MV review rounds, still aren't working well.
