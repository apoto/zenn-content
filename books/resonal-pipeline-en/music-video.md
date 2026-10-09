---
title: "B-5. Music Video (MV) — Start from the Template, Then Reshape It"
---

This chapter explains how the music video (MV) is made. The public version includes an MV template, so you can make one video with it right away. But what I want to share is less what's inside the template and more how to think when you reshape it into the form you like. You say what you want in words, and the AI translates it into 18 axes and a dictionary of effects. This approach works for any kind of video you make.

## Flow

1. Choose a look (optional): only when you say "I want a different style" does the AI list candidates
2. Make a background video (optional): only when you've chosen a video generation service, a short looping video is made from the cover image
3. The AI makes one MV with the template: it times when the lyrics appear, measures the tempo, renders the video, and checks that nothing is broken
4. You watch it and say whether it's OK or what you want to fix
5. The AI fixes it. Steps 4 and 5 repeat until you say OK

## First, make one with the template

I make the MVs with Remotion. Remotion is a library that draws screens written as React components one frame at a time and turns them into video. Since the screen is code, the AI can fix the video just by rewriting the code.

![](/images/resonal-pipeline/remotion-code.jpg)
*A RESONAL MV on screen. Code on the left, the Remotion Studio preview on the right.*

In the MV step, the AI makes one MV with the template. It transcribes the vocals to time the lyrics, measures the tempo and intensity of the audio, and decides the camera moves. It renders the main video, a vertical short, and a thumbnail, and checks that the videos aren't broken. Even with no instructions, you get a finished video.

## The template is a starting point

The finished MV is only a starting point. If you say "I want the camera to move in closer in the chorus" or "I want the text in a Mincho (serif) font", the AI rewrites the matching part of the template and makes it again. You don't need to remember which file to change or how.

## When you reshape it, say it in words. The AI translates it into the axes and the effects dictionary

If you say "make it cooler", the AI doesn't know what to change. So the public version includes two tools for making the look concrete: 18 axes that split up "what to decide", and a dictionary of effects that collects the options for "how to show it".

The **18 axes** are the list of things you decide for an MV. It doesn't mean there are 18 ways to show it.

| Category | Axes | Example options |
|---|---|---|
| Lyrics (6) | Layering, placement, typeface, entrances/exits, decoration, band | Placement: center / bottom band / vertical text on the left and right edges. Typeface: extra-bold gothic / Mincho / round pop |
| Character (6) | Whether to show, source material, movement, composition, foreground separation, expression | Movement: breathing only / bouncing on the beat / moving at the joints |
| Background (4) | Source material, switching, screen effects, camera | Camera: slow move / push-in / orbit / whip pan |
| Hits (2) | Where to put them, how to release | Chorus only / whole song. Blackout / light wipe / negative invert |

The **effects dictionary** holds what goes into each axis. It contains 92 entries: 73 effects and 19 scenes. The effects are split into 8 categories: camera, editing, light and color, effects, text, composition, motion, and UI. The scenes collect combinations of light and effects for each kind of place, like underwater, a rainy city, or a train platform. Each entry describes what happens, which emotions and timing it fits, the numbers for building it, which effects it pairs well or badly with, and a checklist for the result. It's in `direction-library/` in the public version.

But you don't need to memorize the 18 axes or the 92 entries and pick from them. You just say what bothers you or what you want, in words. The AI translates that into axis values and effects from the dictionary, writes them into a per-section direction sheet (`DIRECTION.md`), and rewrites the template. It's mostly the AI that looks things up in the dictionary.

For example, with Dive Reflex, this is what I said. I wasn't thinking about the dictionary at all.

| What I said | Axis values the AI chose | Dictionary entries the AI used |
|---|---|---|
| "I think switching between the surface and underwater is hard, so you don't have to force those moments." (水面と水中の切り替えは難しいと思うから、その瞬間は無理にとらなくていいよ) | How to release hits = light wipe. Don't show the moments of hitting the water, diving, or surfacing; connect them with cuts and light | `light-flood-wipe` (wash the screen with light to switch) / `crash-zoom` (sudden push-in on surfacing) |
| "Could you also shoot footage of 彩瀬?? swimming, from her point of view?" (彩瀬主観で泳いでる映像も撮れるかな？) | Background camera = swimming in first person, only during the instrumental break | `pov-shot` (point-of-view shot) / `orbit` (orbit) |
| "Let's drop the dancing altogether. The world is so beautiful, I don't want to break it." (ダンスはそもそも不要にしよう。せっかく綺麗な世界観だから壊したくない) | Character movement = quiet acting (sitting and swinging her legs, a hand on her chest, holding up grains of sand) | `breathing-idle` (still, breathing only) |
| "Since things like baseball sounds show up in the lyrics, I pictured it as a song about a river or something like that." (野球の音とか歌詞に出てくるってことは、わりと川とかの歌なのかなーってイメージした) | Background material = an inlet with the opposite shore close by (seawall, utility poles, house lights). Add a close-up of a radio | Scene `beach-sunset` (a waterside at dusk) |

For axes I said nothing about, the AI decides from the song and the images, and writes down the reason. For example, the center of the screen was the boundary of the water surface and the place where the character sits, so the lyrics were moved to the bottom band, in thin white Mincho so they wouldn't look out of place on the realistic scenery. In Dive Reflex, the AI used 24 effects and 2 scenes from the dictionary this way, section by section. If you also write "default" for axes you leave at the default, you can tell apart "not decided yet" from "chose the default".

This approach works for any video. Rhythm-game song or ballad, with or without a character, the things to decide are the same 18 axes. After the first MV is done, the AI tells you, "From here you can reshape it with the axes and the effects dictionary." If you'd like to browse the dictionary and pick yourself, say "I want to choose the look of the MV", and the AI will go through the axes with you one by one using the skill `mv-styles`.

## Using and reshaping RESONAL's 13 styles

At RESONAL, I give names to combinations of axes I use often and call them "styles". Things like "white shapes and extra-bold gothic with black-and-white inversion" or "flying through a 3D world with a camera". As of October 2026, there are 13.

![Dive Reflex (lowpoly-corridor). She dives from a pier in the evening, lies on her back at the bottom, and floats up to the night water surface](/images/resonal-pipeline/style-dive-reflex.jpg)
*Dive Reflex (lowpoly-corridor). She dives from a pier in the evening, lies on her back at the bottom, and floats up to the night water surface*

You can see the 13 styles and the default template, with images, in the next chapter, ["B-5 Supplement. Style Gallery"](https://zenn.dev/apoto/books/resonal-pipeline-en/viewer/style-gallery).

The code for these 13 styles is also in `styles/` in the public version. I'm sharing them while they're still a work in progress, so the steps and structure differ from style to style, but feel free to use them as they are.

When they start to feel like not enough, you can add your own ideas. You can make a new style in `styles/`, change an existing style, or add one new effect to the effects dictionary, all following the same axes and dictionary format. Of course, you can also reshape the workflow itself into something completely new.

## You watch it and fix it

When the MV is ready, the AI lines up the main video, the short, and the thumbnail, asks "Please watch them and tell me whether they're OK or what you want to fix", and stops. This is one of the places where you make the call.

When you say what you want to fix, the AI suggests 2–3 ways to fix it, rewrites using the one you pick, and makes it again. You can go back and forth as many times as you like. Once you say OK, the MV step is done.

### If you don't like something, don't hold back

If something in the first draft bothers you, say so without holding back. Your instructions can fix it. When you do, add "just this song, or from the next song on too", so the AI can choose where to make the fix. If you don't say, the AI will ask.

**Fix it for this song only**: the AI rewrites the settings of this song's project. The next song isn't affected.

```
Around 2:29, the main subject of the image goes off screen. Move in so the subject stays in frame
For this song only, tone down the white flash at the start of the chorus
Make the lyric text one size bigger
```

**Keep it the same from the next song on**: the AI fixes the template or the style. That doesn't reach songs that are already finished, so it applies the same fix to the current song too.

```
Fix the template so the gauge-like display in the top right doesn't appear from the next song on
Keep the white flash at the start of the chorus weaker from now on, starting with the next song
```

**Keep it as a new look**: give a name to the look you reshaped this time and save it as a style.

```
Add this time's look to styles/ as a new style
```

For setting values like the artist name, the credit text, or the loudness, the AI edits `workflow.config.json`. If you say "I want to redo the setup", it asks you only about that item again.

## Want to know more? Ask the AI

For how the template works, or what's inside the 18 axes and the effects dictionary, try asking the AI.

```
Tell me the steps used to make this MV
Suggest effects from the effects dictionary that fit the chorus
```

## Summary

The MV is a step where you make one video with the template, then reshape it freely. When you reshape it, say what you want in words, and the AI translates it into the 18 axes and the effects dictionary and rewrites the template. RESONAL's 13 styles can be used as they are, and when they feel like not enough, you can make new ones or change them using the same format.
