# OpusClip (clipping tool)

## Cost

- At least 10 credits per video, then about 1 credit per minute of source video. Check the
  remaining credits first with the usage tool, and say the cost before submitting.
- For a long video, offer to clip only part of it (a start and end time) to use fewer credits.

## Submitting

- Links: YouTube, Vimeo, Zoom, Facebook, LinkedIn and a few other video sites; unlisted is
  fine. OpusClip refuses Google Drive links, direct download links included, and Dropbox is
  not on its list.
- A file instead of a link: get an upload link from OpusClip, upload the file to it, and
  submit with the upload id. This needs network access to storage.googleapis.com, which
  Claude in the browser does not have by default. If the upload is blocked, ask for a link
  instead. The file must have a sound track.
- Use the brand's template from the brand templates list, and call it by its name. The list's
  caption style can be out of date. If only OpusClip's presets exist, say so before using one.
- Submit in clipping mode: the video link, the clipping instruction as the custom prompt, the
  template, portrait, clips of 15 to 30 seconds, captions on.
- Do not use the modes that keep the whole video or skip curation when the person wants
  several clips: both return one full-length video.

## Waiting and reviewing

- An empty clip list while the project is still in progress means the clips are not ready.
  Check again rather than concluding there are none.
- Show the clips with the preview tool, so the person can watch them in the conversation.

## Exporting

- Export each approved clip in HD. If the export says it is rendering, ask again in a few
  seconds until it is ready.
- HD files are large, around 30 MB for a 25-second clip.
- Clips finish in OpusClip. Its links carry a signature with `~` characters that breaks when
  another tool encodes them, so Canva cannot import them; see `canva.md`.
