# Checks for make-creatives

Run these in a new chat with the plugin installed, on the Plug Demo workspace, before merging a
change to `main`. Steps 5, 6 and 11 stop at the cost question and step 8 before the ad is made, so the whole run is free; answer "not
now" there.

| # | You type | It passes when the agent |
|---|---|---|
| 1 | "What static creatives should we make next? Plug Demo." | Shows one table of Plug Demo's static briefs in Plug's order with their exact titles and what each is for, leaves out disliked, expired and retired ones, shows no rank, and does not lead with the brand. |
| 2 | Pick one brief | States the export cost first, then opens the ratios in the design tool as one editable design named after the brief. |
| 3 | "Put the headline at the top and make it shorter" | Makes the edit, saves, points out any clear mistake against the brief, and gives the link with what changed. |
| 4 | "What works in our video creatives?" | Names what works and what does not, from Plug's reads, with the window. |
| 5 | "Make short ads from this video: <link>. It's a stage interview, for awareness." | Asks whether the brand may use it, reads Plug for attention, shows a clipping instruction fitted to the video, names the brand's template, states the cost, and stops. |
| 6 | "Make a video from Plug's top video brief" | Takes the first video brief in Plug's order without showing a rank, and shows a prompt that carries every frame's timing and description word for word, the storyboard and the kit's logo as reference images, sound only as the storyboard says, and no on-screen text. States the cost and stops. |
| 7 | "What carousel creatives should we make?" | Says Plug has none that fit and offers to have Plug write one. |
| 8 | After step 3 | Offers to launch it paused: with an ads tool connected, names the fitting ad set, shows the ad copy and stops at the yes; without one, hands over the file, the copy and the ad set name. |
| 9 | Pick a brief that has comments on Plug Demo | Reads the brief's comments, applies them without asking the person to repeat them, and says so once if one goes against the brand. |
| 10 | After step 3 | Saves the design's link on the brief as a comment, says so, and sets no like or dislike. |
| 11 | "Send frame 3 of Plug Demo's top video brief to Canva" | Names frame 3 from the brief (number, title, timing), states the cost first (one export for the whole storyboard), exports only that frame as 9:16, opens it as one design named `<brief title> | frame 3`, and gives the link. |
| 12 | After step 3: "Make a Portuguese version" | Duplicates the pages, changes only the text, says a native speaker should check it, saves the link on the same brief as `Design (Portuguese): <link>`, and makes no new brief. |
| 13 | Upload a competitor's static: "Make our version" | Offers a Plug brief from the file or making it now. Making it now, reads the brand and Plug's winning and losing elements, keeps the ad's look and how its message is built, uses none of the other brand's text, logo, people or product, and gives the design link. |
| 14 | "Make a 20-second 9:16 video from our best testimonial" | Reads what works for the goal and the brand, says what it will lean on, and makes the cut itself or with a connected editor it names, without defaulting to a design tool or calling a connected tool wrong. Ends on the brand's end card if the kit has one, asks the person to watch it, and offers the launch. |

Write pass or fail per step in the pull request. A failure is fixed in the skill and only that
step is run again.
