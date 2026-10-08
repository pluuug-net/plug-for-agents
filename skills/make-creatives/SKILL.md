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
   when the person asks. Text goes on in the design tool, never inside a generated video:
   video models garble letters. The logo may appear in a generated video only on the product,
   such as a phone screen or a car, and only from the brand kit's logo image.
3. **Show briefs in Plug's order, as Plug names them.** One table of every brief that fits, in
   the order Plug returns them: its exact title, the format, what it is for in plain words
   (purchases, site visits, attention), the date and its Plug link. Leave out briefs marked
   disliked or expired, or whose approach is retired. When the person asks for one brief, take
   the first that fits the format and goal they named. Do not rename a brief, show Plug's
   ranking, or invent why Plug suggests it.
4. **Name what you make after the brief.** Every design and file takes the brief's exact title,
   with the ratio added when there is more than one (`<brief title> | 9:16`). Clips made without
   a brief keep the clipping tool's titles.
5. **Speak in the person's words.** Never pass on Plug's internal labels, statuses or codes,
   even reworded: review states, funnel codes, confidence labels. Raise a problem only when the person has to
   act on it, once and plainly. Fix small faults yourself and say what you fixed. Plug's
   briefs and files are ready to use; Plug's notes about its own checks are for Plug, not the
   person.
6. **Ask with buttons.** When the person has to choose (a brief, a goal, a yes to a cost), use
   the app's question panel if it has one, with each option as a button.
7. **Ask before spending, and spend once.** Say what a step costs and wait for a yes. Start a
   paid run once and follow it by its id; if a call fails, look for the run before trying
   again. Afterwards say what it cost, from the tool. Each tool's file says how it charges.
8. **Fetch once.** Reuse what a tool already returned in this chat. Call it again only for
   something new, or for fresh links once the old ones expire.
9. **One step at a time.** End each step with a result the person can open or play in one
   click, then wait for them to choose or say what to change.
10. **Links expire.** Plug's files and generated videos last about an hour, so move each one on
   in the same step it is made.
11. **This ends at a finished creative.** Saving it and launching it are the person's own steps.

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
   every clip, best fit first: title, length, a short verdict against what works and what the
   clips are for, and the clip's own link to play it. Show previews only when the person asks.
5. Export the clips the person picks in HD. End with the download links (they expire) and the
   clipping tool's link, where the clips stay.

## 3. A short video from a video brief

1. `plug_list_creative_briefs`: show the video briefs as rule 3 says. The person picks one.
2. `plug_get_creative_brief`: the storyboard frames (timing, description, on-screen text and
   audio), the CTA, and the storyboard image in `generated_assets`.
3. Write the video prompt from the storyboard without rewriting it:
   - the storyboard image as the first reference image, and each frame in order with its
     timing and description, word for word. Say that the image shows the frames side by side,
     each one a full-screen shot in turn, and that the words on and under the frames are notes,
     not part of the picture;
   - the brand kit's logo image as the second reference image, shown only where a frame puts
     it on the product;
   - sound as the storyboard says: each spoken line in double quotes, and music and sound as
     described. If the storyboard has no audio, the video has no sound;
   - "no on-screen text, captions or letters": the frames' on-screen text is the person's to
     add in the design tool.

   Include people only if the brand's people policy allows them.
4. Show the prompt and the cost, and on a yes generate it: 9:16, as long as the frame timings
   add up to. If the run fails on the storyboard image (the model refuses real-looking people),
   say so and run it once more without that image, from the frame text and the logo alone.
5. Give the link where the person can play it, and ask them to look for letters, extra people
   or a warped logo: you cannot watch it. Make a new take only after a yes, because it costs
   again.
6. Put the video into the design tool: one 9:16 design named after the brief, the video filling
   the page and nothing else. Save, give the link, and list the storyboard's on-screen lines
   with their timings for the person to add.

## End with

What was made, its link, what it cost, and what the person does next.
