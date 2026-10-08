# Seedance 2.5 on Replicate (video model)

## Cost and time

- About €0.20 per second of 720p video. An 8-second video takes about 5 minutes.
- Say the cost before every run, including a new take.

## Running it

Run Replicate's official model `bytedance/seedance-2.5` with:

- `prompt`: the shot-by-shot prompt, naming the mood board as [Image1]
- `reference_images`: the mood board link (reference images cannot be combined with a first
  or last frame image)
- `duration`: the sum of the frame timings, up to 30 seconds
- `resolution: 720p`
- `aspect_ratio: 9:16`
- `generate_audio: true`

## After it runs

- Replicate deletes the output after one hour. Move it into the design tool in the same step,
  or give the person the link to download within the hour.
- Check the take for garbled text, extra people and warped logos before showing it.
