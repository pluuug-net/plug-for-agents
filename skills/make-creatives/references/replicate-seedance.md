# Seedance 2.5 on Replicate (video model)

## Cost and time

- About €0.20 per second of 720p video. An 8-second video takes about 5 minutes.
- Say the cost before every run, including a new take.

## The prompt from a Plug video brief

Write it from the brief's storyboard (`plug_get_creative_brief`) without rewriting it:

- the storyboard image as the first reference image, and each frame in order with its timing and
  description, word for word. Say that the image shows the frames side by side, each one a
  full-screen shot in turn, and that the words on and under the frames are notes, not part of
  the picture;
- the brand kit's logo image as the second reference image, shown only where a frame puts it on
  the product (a phone screen, a car);
- sound as the storyboard says: each spoken line in double quotes, and music and sound as
  described. If the storyboard has no audio, the video has no sound;
- "no on-screen text, captions or letters": the frames' on-screen text is added afterwards;
- people only if the brand's people policy allows them.

Generate 9:16, as long as the frame timings add up to. Afterwards list the storyboard's
on-screen lines with their timings, for adding in the editing step.

## Running it

Run Replicate's official model `bytedance/seedance-2.5` (`create_models_predictions`) with:

- `prompt`: the prompt below, naming the storyboard image as [Image1] and the
  logo as [Image2]. Spoken lines go in double quotes: the model speaks them.
- `reference_images`: the storyboard image link, then the brand kit's logo image link (the
  reference image of kind `logo`, else the first one in the logo slot), in that order (reference images cannot be combined with a first or last frame image)
- `duration`: the sum of the frame timings, 4 to 30 seconds
- `resolution: 720p`
- `aspect_ratio: 9:16`
- `generate_audio`: true when the storyboard has audio, false when it has none

Do not wait for it in the same call (no `Prefer: wait`): it takes minutes, the call times out,
and a retry starts a second paid run. Keep the run's id and check it with `get_predictions`.
If a call fails, find the run with `list_predictions` before starting another.

The model refuses some storyboard images, often ones with real-looking people, and the run
ends as failed. Replicate does not charge a failed run, so the person's yes covers one more run
without the storyboard image: drop it from `reference_images` and from the prompt, keep the logo
as [Image1] and every frame's text.

## After it runs

- The person plays it on the run's Replicate page (`urls.web`).
- Replicate deletes the output after one hour. Move it into the design tool in the same step,
  or give the person the link to download within the hour.
