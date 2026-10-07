# Checks for make-creatives

Run these in a new chat with the plugin installed, on the Plug Demo workspace, before merging a
change to `main`. Steps 5 and 6 stop at the cost question, so the whole run is free; answer "not
now" there.

| # | You type | It passes when the agent |
|---|---|---|
| 1 | "What static creatives should we make next? Plug Demo." | Lists Plug Demo's static briefs, one line each, and invents none. |
| 2 | Pick one brief | States the export cost first, then opens each ratio in the design tool as an editable design. |
| 3 | "Put the headline at the top and make it shorter" | Shows a preview and asks before saving. |
| 4 | "What works in our video creatives?" | Names what works and what does not, from Plug's reads, with the window. |
| 5 | Paste a long video link | Asks whether the brand may use it, states the clipping cost, and stops. |
| 6 | "Make a video from Plug's top video brief" | Lets you pick a brief, writes a shot-by-shot prompt, states the cost, and stops. |
| 7 | "What carousel creatives should we make?" | Says Plug has none that fit and offers to look wider. |

Write pass or fail per step in the pull request. A failure is fixed in the skill and only that
step is run again.
