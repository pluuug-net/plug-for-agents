---
name: make-creatives
description: Makes paid social creatives for Meta and TikTok from Plug, one step at a time. A static from a Plug brief, short clips cut from a long video and steered by what works in the account, or a short video from a Plug video brief, each finished in the team's own design, clipping or video tool. Use when someone asks what creatives to make next, or asks for a static, clips or a short video for their brand.
---

# Make creatives from Plug

Plug decides what to make next, from what works and what does not in the account. The team's
own tools make it. The person approves every step.

## What this needs

- **Plug's connector.** Every use case starts there.
- **A tool for each job**, connected by the team. Today's defaults, each with a file to read
  before first use:
  - design tool: Canva, `references/canva.md`
  - clipping tool: OpusClip, `references/opusclip.md`
  - video model: Seedance 2.5 on Replicate, `references/replicate-seedance.md`

  If the team uses another tool for a job, follow the same steps with it.

## Rules

1. **Start from Plug.** Use a Plug brief, or Plug's read of what works and what does not. Never
   present a brief as Plug's unless Plug returned it. If nothing fits, say so and look wider:
   older briefs, another format, a longer window.
2. **The brand is a hard rule.** Call `plug_get_brand` first. Its colours, fonts, logo, claims,
   CTAs, people policy, and do's and don'ts all apply. Text and logos go on in the design tool,
   never inside a generated video.
3. **Ask before spending.** Say what a step costs and wait for a yes. Each tool's file says how
   it charges.
4. **One step at a time.** Show the result, then wait for the person to choose or say what to
   change.
5. **Links expire.** Plug's files and generated videos last about an hour, so move each one on
   in the same step it is made.
6. **This ends at a finished creative.** Saving it and launching it are the person's own steps.

## 1. A static from a brief

1. `plug_list_creative_briefs`: show the top static briefs, one line each, with the title and
   why Plug suggests it. The person picks one.
2. `plug_get_creative_brief`: what to make, the copy, the CTA and the finished images.
3. `plug_export_brief_files`: say the cost first (each new PSD uses 1 of the workspace's
   monthly exports, and a repeat within a day is free). Flag any file marked `held`: it failed
   Plug's quality check.
4. Open each ratio's PSD in the design tool as an editable design named
   `<brief title> | <ratio>`. The image and the headline arrive as separate layers.
5. The person says what to change, and you make the edits. Show the preview, and save only
   after a yes.

## 2. Short clips from a long video

1. `plug_list_winning_tags` and `plug_list_losing_tags` with `metric: hook_rate`, and
   `plug_list_creative_approaches` with `media_type: video`. Say in one sentence what works,
   and what does not, in the account's videos.
2. Ask for the video link. Confirm the brand may use it and everyone in it agreed.
3. In the clipping tool: pick the brand's template, state the cost, and on a yes submit the
   video with what works as the clipping instruction, portrait, 15 to 30 second clips,
   captions on. It renders in the background.
4. When the clips are ready, show the top three and say for each why it matches what works.
5. The person approves, and you export each approved clip in HD.

## 3. A short video from a video brief

1. `plug_list_creative_briefs`: show the video briefs. The person picks one.
2. `plug_get_creative_brief`: the storyboard frames (timing, on-screen text, description),
   the CTA, and the mood board in `generated_assets`.
3. Write one prompt, shot by shot, from the frame timings, in the mood board's look. Add "no
   on-screen text, captions or letters". Include people only if the brand's people policy
   allows them, and a voice only if the brand allows one; otherwise music and sound only.
4. State the cost, and on a yes generate it: 9:16, as long as the frame timings add up to.
5. Show the video and name any problem (garbled text, extra people, a warped logo). Make a new
   take only after a yes, because it costs again.
6. In the design tool, put the video into a 9:16 design with the brand kit and add the
   headline in the brand font. Show the preview, save after a yes, and export an MP4. Add no
   end card unless the person asks for one.

## End with

What was made, its link, what it cost, and what the person does next.
