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
- **Load a use case's tools in one search**: the Plug tools named in its steps, and the tools
  named in that tool's file.

## Rules

1. **Start from Plug.** Use a Plug brief, or Plug's read of what works and what does not. Never
   present a brief as Plug's unless Plug returned it. If nothing fits, say so and look wider:
   older briefs, another format, a longer window. If still nothing fits, offer an idea from the
   brand kit, and say it is not from Plug's data.
2. **The brand is a hard rule.** Call `plug_get_brand` before making anything, not before
   choosing. Its colours, fonts, logo, claims, CTAs, people policy, and do's and don'ts apply
   to everything you make and every edit, so check the result against them. Break one only
   when the person asks. Text and logos go on in the design tool, never inside a generated
   video: video models garble letters and logos.
3. **Show briefs as Plug names them.** One table of every brief that fits: its exact title, the
   format, the date and its Plug link. Leave out briefs marked disliked or expired, or whose
   approach is retired. Do not rename a brief or invent why Plug suggests it.
4. **Speak in the person's words.** Never pass on Plug's internal labels, statuses or codes:
   review states, funnel codes, confidence labels. Raise a problem only when the person has to
   act on it, once and plainly. Fix small faults yourself and say what you fixed.
5. **Ask before spending, and spend once.** Say what a step costs and wait for a yes. Start a
   paid run once and follow it by its id; if a call fails, look for the run before trying
   again. Afterwards say what it cost, from the tool. Each tool's file says how it charges.
6. **One step at a time.** End each step with a result the person can open or play in one
   click, then wait for them to choose or say what to change.
7. **Links expire.** Plug's files and generated videos last about an hour, so move each one on
   in the same step it is made.
8. **This ends at a finished creative.** Saving it and launching it are the person's own steps.

## 1. A static from a brief

1. `plug_list_creative_briefs`: show the static briefs as rule 3 says. The person picks one.
2. `plug_get_creative_brief`: what to make, the copy, the CTA and the finished images.
3. `plug_export_brief_files`: say the cost first (each new PSD uses 1 of the workspace's
   monthly exports, and a repeat within a day is free).
4. Open the PSDs in the design tool as one editable design named after the brief, one page per
   ratio. The image and the headline arrive as separate layers.
5. The person says what to change. Make the edits, save, then look at the result and point out
   any clear mistake: text cut off or overlapping, a colour or font off brand, or anything that
   goes against the brief and its composition. Show the design in the chat if you can, and give
   its link with what changed, before and after.

## 2. Short clips from a long video

1. Ask for the video (a link, or a file they upload in the clipping tool) and what the clips
   are for (attention, site visits or purchases), unless the person said. Confirm the brand may
   use the video and everyone in it agreed.
2. Read what works in videos for that goal: `plug_list_winning_tags`, `plug_list_losing_tags`
   and `plug_list_creative_approaches` with `media_type: video`, in the comparison group for
   that goal, on the metric it is judged by (attention: hook rate; visits: CTR; purchases: CPA
   on the purchase event). If the read is thin, include paused creatives, but never leave the
   goal's group; if it is still thin, say Plug has no clear read for this goal yet. Say in a
   few lines what works and what does not, leading with what Plug is most sure of.
3. Understand the video first: what kind it is, who speaks and about what, from what the
   person says and the video's title. Write the clipping instruction as what works, put as
   moments this video can contain, adding nothing Plug did not find. Show the instruction, the
   brand's template and the cost, and on a yes submit: portrait, 15 to 30 second clips,
   captions on. Say when to check back: rendering takes about 10 minutes.
4. When the clips are ready: the link to all clips in the clipping tool, then one table of
   every clip, best fit first: title, length, and a short verdict against what works and what
   the clips are for. Show the best fits as previews.
5. Export the clips the person picks in HD. End with the download links (they expire) and the
   clipping tool's link, where the clips stay.

## 3. A short video from a video brief

1. `plug_list_creative_briefs`: show the video briefs as rule 3 says. The person picks one.
2. `plug_get_creative_brief`: the storyboard frames (timing, on-screen text, description),
   the CTA, and the mood board in `generated_assets`.
3. Write one prompt, shot by shot, from the frame timings, in the mood board's look. Add "no
   on-screen text, captions or letters" unless the person wants text in the video; then warn
   once that the model garbles letters. Include people only if the brand's people policy
   allows them, and a voice only if the brand allows one; otherwise music and sound only.
4. State the cost, and on a yes generate it: 9:16, as long as the frame timings add up to.
5. Give the link where the person can play it, and ask them to look for garbled text, extra
   people or a warped logo: you cannot watch it. Make a new take only after a yes, because it
   costs again.
6. Offer to finish it in the design tool, and recommend it when the brief has on-screen text:
   a 9:16 design with the brand kit and the headline in the brand font. Save, give the link and
   say what is on it, and export an MP4 after a yes. Add no end card unless the person asks.

## End with

What was made, its link, what it cost, and what the person does next.
