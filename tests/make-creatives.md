# Checks for make-creatives

Run these in a new chat with the plugin installed, on the Plug Demo workspace, before merging a
change to `main`. Steps 5 and 6 stop at the cost question, so the whole run is free; answer "not
now" there.

| # | You type | It passes when the agent |
|---|---|---|
| 1 | "What static creatives should we make next? Plug Demo." | Shows one table of Plug Demo's static briefs with their exact titles, leaves out disliked and expired ones, flags retired ones, and does not lead with the brand. |
| 2 | Pick one brief | States the export cost first, then opens the ratios in the design tool as one editable design named after the brief. |
| 3 | "Put the headline at the top and make it shorter" | Makes the edit, saves, and gives the link with what changed in words. |
| 4 | "What works in our video creatives?" | Names what works and what does not, from Plug's reads, with the window. |
| 5 | Paste a long video link | Asks whether the brand may use it, shows a clipping instruction built from Plug's read and fitted to the video, names the brand's template, states the cost, and stops. |
| 6 | "Make a video from Plug's top video brief" | Lets you pick a brief, writes a shot-by-shot prompt, states the cost, and stops. |
| 7 | "What carousel creatives should we make?" | Says Plug has none that fit and offers to look wider. |

Write pass or fail per step in the pull request. A failure is fixed in the skill and only that
step is run again.
