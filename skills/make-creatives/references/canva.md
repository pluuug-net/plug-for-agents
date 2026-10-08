# Canva (design tool)

## Opening a Plug brief's PSD

- Use Canva's tool that imports a design from a link (currently `import-design-from-url`),
  with the file's `psd_url`. Do not use the tool that uploads an asset: that adds a flat image,
  not an editable design.
- Each import makes one design. Name the first one after the brief, then merge each other ratio
  into it with Canva's merge tool (currently `merge-designs`), one design per call, so it ends
  with a page per ratio. If the merge fails, keep one design per ratio named
  `<brief title> | <ratio>`.
- The image and the headline arrive as separate layers, and the headline stays editable.
- Canva uses its own font unless the brand's fonts are in the team's Canva brand kit. Say so
  if the headline font is not the brand's.

## Editing

- Edit with Canva's editing tool (currently `edit-design`). Canva edits in a draft, and its
  draft previews do not show in Claude's chat. Make the edits, save, and say what changed,
  before and after, with the design's link. The person can undo in Canva.
- New text Canva adds starts small and black. Set its size and colour from the brand kit.

## A video into a design

1. Upload the video to Canva by its link (currently `upload-asset-from-url`), within the hour
   the link lasts. An uploaded video has no link of its own; the saved design is what the
   person opens.
2. Create an empty 9:16 design named after the brief with Canva's design creation tool
   (currently `create-design`, format "Instagram Story"). Never use the design suggestion
   tool (`generate-design`): it returns layouts with text and stock elements to choose from.
3. Open the design for editing, remove anything on the page, place the video so it fills the
   page, and save.
4. Give the design's link. Add no text, logo or end card unless the person asks.

## Links Canva can fetch

- Plug's export links and Replicate's output links work.
- OpusClip's links do not. Their signature contains `~` characters, the link stops working
  once they are encoded, and Canva's download fails even when the link works everywhere else.
  If a clip must go into Canva, the person downloads it from OpusClip and drops it in.
