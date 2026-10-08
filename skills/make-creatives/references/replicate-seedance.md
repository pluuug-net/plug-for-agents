# Seedance 2.5 on Replicate (video model)

## Cost and time

- About €0.20 per second of 720p video. An 8-second video takes about 5 minutes.
- Say the cost before every run, including a new take.

## Running it

Run Replicate's official model `bytedance/seedance-2.5` (`create_models_predictions`) with:

- `prompt`: the shot-by-shot prompt, naming the mood board as [Image1]
- `reference_images`: the mood board link (reference images cannot be combined with a first
  or last frame image)
- `duration`: the sum of the frame timings, up to 30 seconds
- `resolution: 720p`
- `aspect_ratio: 9:16`
- `generate_audio: true`

Do not wait for it in the same call (no `Prefer: wait`): it takes minutes, the call times out,
and a retry starts a second paid run. Keep the run's id and check it with `get_predictions`.
If a call fails, find the run with `list_predictions` before starting another.

## After it runs

- The person plays it on the run's Replicate page (`urls.web`).
- Replicate deletes the output after one hour. Move it into the design tool in the same step,
  or give the person the link to download within the hour.
