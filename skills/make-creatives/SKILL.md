---
name: make-creatives
description: Makes paid social creatives for Meta and TikTok with Plug, from the decision of what to make to a launched ad. Plug says what to make, from what works in the account and the brand's rules; Claude or the team's own tools make it; the person approves every step. Use when someone asks what creatives to make next, or asks for a static, a video, clips or a new version of an ad for their brand.
---

# Make creatives with Plug

Plug decides what to make, holds the brand and knows where it runs. Claude or the team's own
tools make it. Every creative ends launched, and the person approves every step.

## What Plug brings

Read these from Plug before making anything. They are why the creative is worth making.

| Plug gives | Tools |
|---|---|
| What to make: a ready brief, or a new one Plug writes from the person's words, idea or file | `plug_list_creative_briefs`, `plug_get_creative_brief`, `plug_create_brief_drafts` (see the `plug` skill) |
| What works and what does not for this goal: elements, approaches, winning and losing creatives | `plug_list_creative_elements`, `plug_list_creative_approaches`, `plug_list_winning_media` |
| The brand: rules, claims, CTAs, colours, fonts, logo, people policy, and its own photos and videos | `plug_get_brand` |
| Files ready to edit: a brief's image in any ratio, a video frame, a blank video page | `plug_export_brief_files` |
| Where the result goes back: the brief, so the team finds it and Plug learns from it | `plug_update_creative_brief` |

## The loop

Every creative, static or video, from a brief or from the person's own material, follows these
steps:

1. **Goal.** What it is for (attention, site visits, leads, purchases), the format, and where
   it runs. Ask only what the person has not said.
2. **Read Plug.** A brief that fits first, in Plug's order and with its exact title. If none fits,
   offer to have Plug write one. If the person brings their own material, still read what works
   for that goal and the brand, and say in a few lines what to lean on and what to avoid,
   leading with what Plug is most sure of. If the read is thin, say so.
3. **Make it.** Take the most direct route to a finished file (see below). Show the plan and
   what it costs before you start.
4. **Check it.** Hold the result against the brand and against what works: text cut off or in
   the platform's safe zones, colours, fonts and logo off brand, a claim or CTA the brand does
   not allow, anything against the brief. Fix what you can and say what you fixed. You cannot
   watch a video, so ask the person to watch it before launch. A version in another language
   changes only the text and keeps the image, layout and brand; say a native speaker should
   check it, and add the translated file to the brief it came from using the same finished-file upload.
5. **Launch it.** Put it in the right ad set with primary text, headline and description: the
   wording of the ads already linked to the brief when `plug_get_ad_launch` offers it, else written
   from the brief in the brand's words. Where Plug can launch (`plug_get_ad_launch` says so), use
   `plug_create_ads`: it makes one ad per brief in each ad set the person picks, with every size of the
   files, paused or live as they choose, and links each ad to its brief. Otherwise use a connected ads
   tool, paused. If none can create ads, hand over the file, the copy and the ad set name, ready to
   upload. The person always agrees before an ad is made.
6. **Close the loop.** Upload the finished files with `plug_create_brand_images(target="brief_final")`.
   Pass the returned upload IDs to `plug_update_creative_brief(add_files=...)` for the original brief.
   After a tool other than `plug_create_ads` creates ads from the brief, call
   `plug_update_creative_brief(link_ads=...)` with their platform and ad IDs in the same turn, including
   paused ads. Plug links the ads that `plug_create_ads` makes. If the person made their own
   version of an ad they saw, offer to add it as a new brief with `plug_create_briefs_from_creatives`.
   Leave feedback and approval to the person.

## Making

No tool is the default and none is wrong for a job. Use what the person has and what gets a
finished file fastest:

- **Claude itself**, where it can run code: cut, trim, join, reframe and caption video, place a
  logo and an end card, lay out text on an image. Use the brand's own photos and videos from
  Plug first, and ask the person only for what Plug lacks.
- **The team's connected tools**: a design tool, a video editor, a clipping tool, an image or
  video model. Ask which one they use when more than one could do the job.
- **A video model** only for footage the brand does not have, and only within its people policy.

Before first use of a tool, read its file in `references/` for its known traps. A tool with no
file works the same way, through its own instructions.

## Rules

1. **Start from Plug.** Never present a brief or a read as Plug's unless Plug returned it. If
   nothing fits, say so and offer to have Plug write a brief.
2. **The brand is a hard rule.** Call `plug_get_brand` before making anything. Its rules apply
   to everything you make and every edit. Break one only when the person asks. Never put text
   inside a generated image or video: add it afterwards. When the person brings another
   brand's ad, keep its look and how its message is built, and never its text, logo, people
   or product.
3. **Apply the brief's comments** without asking the person to repeat them. If a comment goes
   against the brand, say so once and follow the brand.
4. **Name what you make after the brief**, with the ratio when there is more than one
   (`<brief title> | 9:16`).
5. **Speak in the person's words.** Never pass on Plug's internal labels, codes or statuses.
   Raise a problem only when the person has to act on it, once and plainly.
6. **Ask before spending, and spend once.** Say what a step costs and wait for a yes. Start a
   paid run once and follow it by its id. Afterwards say what it cost.
7. **One step at a time.** End each step with something the person can open or play in one
   click, and wait for their choice. Ask with buttons when the app has them.
8. **Links expire.** Plug's files and generated outputs last about an hour, so move each one on
   in the same step.
9. **Use the brand's material with permission.** For any video or photo of real people the
   person brings, confirm the brand may use it.

## End with

What was made, where it runs (or is ready to run), its link, what it cost, and what the person
does next.
