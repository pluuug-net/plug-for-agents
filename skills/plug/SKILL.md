---
name: plug
description: >
  Work with Plug's MCP tools: read a paid-social account's action recommendations (Moves),
  creative approach performance, winning and losing creatives and elements, creative briefs,
  the brand (profile and kit) and the documents Plug has published for the customer (Pulse, competitor
  reports). Use when the user asks what to do on their ad account or how their creatives
  perform. To make creatives from Plug's briefs, use the make-creatives skill.
---

# Working with Plug

Plug is an AI performance marketer for paid social. Its MCP tools return conclusions, not raw
metrics: what to do next (Moves), which creative approaches and elements win or lose and why,
what to make next (creative briefs), the brand rules production must follow (brand profile and kit), and
the documents Plug has published for this customer (Pulse, competitor reports).
Everything is scoped to the workspaces the user's Plug account can access, and everything is
read-only except the brand tools (rule 2a). No tool ever changes an ad account.

## Operating rules

1. **Start with `plug_overview`** (or `plug_whoami`) to get the advertiser ids you may read.
2. **No Plug tool changes an ad account.** Nothing here creates, pauses or edits a campaign, ad
   set or ad. Never claim an action was taken on Meta through Plug.
2a. **The brand tools write to Plug.** `plug_update_brand`, `plug_create_brand_images`,
   `plug_update_brand_image` and `plug_delete_brand_image` change the settings Plug's own creative
   work is generated from, and the client asks the user before each one runs. Before an update,
   read the current values with `plug_get_brand` and tell the user what will change; after it,
   report the before/after the tool returns.
3. **Quote the population next to every figure.** The approaches, media and tags tools all
   return one `population` block (scope, window, event, filters, comparison group, benchmark)
   and its one-line `description`; every row carries the same line as `measured_on`. Say it
   next to the numbers. A number without its population is a wrong answer waiting to happen.
   The three tools share one rulebook, read from the Creatives page itself: the ad account is
   the dominant one unless you name it, the window is the last 30 days unless you set it,
   paused media are excluded unless you turn `active_only` off, a CPA is always one named
   event, and a ranking is inside ONE comparison group (funnel | event | audience | format,
   the unit every verdict is made in) with that group's typical ad (`benchmark.median`) and
   average (`benchmark.mean`) as the yardstick. Pass `comparison_group='all'` to see every
   group, and then compare within a group only, never across.
4. **Never blend events or budgets.** `kpi_spend` is non-blended (only media optimising for the
   named event); `totals.spend_all_events` is blended. Present each as itself. Conversion counts
   for different events are never added together.
5. **Use the page's own verdict words** (Winner / Test / Loser / Unclear / Mixed / No verdict),
   never the colour codes.
6. **The CSV export is a file, not an answer.** `plug_export_creative_tags` returns a single-use
   download link (valid 60 minutes). Save the file and analyse it on disk; never read the CSV
   back into the conversation. When the user wants an answer about winning elements, use
   `plug_list_winning_tags` / `plug_list_losing_tags` instead.
7. **Signed URLs expire.** Brief assets, brand-kit reference images and export links live for
   60 minutes; re-call the tool for fresh URLs instead of retrying dead ones.
8. **Visuals render in MCP-Apps hosts** (claude.ai web, Claude Desktop). In other hosts the same
   tools still return every URL; link them instead of describing missing images as an error.
9. **Tag numbers mean two different things.** On the tags tools, `x_lift` is prevalence (how much
   more often the element appears among winners); never present it as a cost multiplier. The
   effect size is `median_metric` vs `sample.median_metric` (the typical ad) and `median_ratio`.
   A `mixed` value is over-represented on one side but its cost disagrees: Plug claims nothing
   about it, and neither should you. Name it as untested, not as a winner or loser.
10. **The tools ask instead of guessing.** A CPA is always one named event: when the user names
   one, pass it as `event`, the same parameter on every creative tool (`event_key` and `kpi`
   still work for one release). One event vocabulary across the three families: reuse
   `population.metric.event_key` from any other Plug answer, and the display name works
   too. When they don't name one, the page resolves one (the account's BOF primary KPI
   setting, else the clearly dominant event) and says how in `kpi_resolution`. If neither is
   clear the tool returns an error `kpi_required` with `available_events`; a label or account
   that does not exist exactly returns an error `scope_required` with `candidates` (never guess
   a label from the user's words, "Sweden" is not a label until the list says so). Your move
   is to ask the user, then call again naming the value exactly as listed. Pass the resolved
   event back when paginating with `cursor`.
11. **Documents arrive as text.** `plug_get_workspace_document` returns a document's extracted
   text (links keep their targets, images become markers). In a client with file access
   (Claude Code, Desktop with shell), prefer downloading `full_text_url` (valid 60 minutes)
   and reading the file from disk for large documents, the same way the CSV export works. If
   `truncated` is true, the inline text is not the whole document: fetch `full_text_url` for
   the rest, or say so and link the document's `url`; never present the cut text as complete.

## Recipe: use a published document (competitor report, Pulse)

1. `plug_list_workspace_documents(advertiser_id)`: what Plug has published for this customer.
2. `plug_get_workspace_document(advertiser_id, slug)`: the document's content as text.
3. Treat a competitor report as evidence for creative decisions: what the competitor runs that
   this account does not (and the reverse), which patterns to avoid fighting head-on, and which
   brief candidates the report's findings support or kill. Cite the report's own numbers, and
   use the preserved links when the user wants to see a competitor's actual ad.

## Recipe: daily account review

1. `plug_list_moves(advertiser_id)`: the open queue, same visibility as the Plug Moves page.
2. `plug_get_move(recommendation_id)` for anything the user wants to act on: full justification,
   target entities, and the triggering issue.
3. Summarise by action type, lead with the highest-impact item, and link each Move's
   `plug_app_url` so the user can review and act in Plug.
4. If the user wants to execute changes (pause, budget), that happens in their own tools (Meta
   Ads Manager, or Meta's own MCP if they have it connected) with explicit human approval per
   change. Plug recommends; the human decides.

## Recipe: make creatives from a brief

Use the `make-creatives` skill, which comes with the Plug plugin
(https://github.com/pluuug-net/plug-for-agents): statics from a brief, short clips from a long
video and short videos from a video brief, finished in the team's own tools.

## Recipe: update the brand from the brand's own documentation

The case this exists for: the customer keeps their real brand guidelines somewhere else and wants
Plug's brand to match.

1. `plug_get_brand(advertiser_id)`: read what Plug currently holds. Note the `version`.
2. Compare it against the source the user gave you (a PDF in the conversation, a page, their own
   words). List the differences for the user before changing anything: what Plug has, what the
   source says.
3. `plug_update_brand(advertiser_id, …)` with only the fields that differ and the `version` from
   step 1; the client asks the user before it runs. Remember the merge rules: objects merge key by
   key, **lists replace whole** (send the full list you want, not just the additions), `null`
   clears a field. A version conflict means somebody edited the brand in the Plug app while you
   were working: re-read and re-apply, do not retry blindly. Report the before/after it returns.
4. Images are separate. `plug_create_brand_images` returns an upload ticket: run the `curl` if
   you have a shell, otherwise give the user the `upload_page` link. Never paste file contents
   into the conversation, and never ask the user to describe an image so you can store the
   description instead of the file.

If the user hands you a brand book and wants Plug to read it, you have two routes. Reading the PDF
yourself and sending the values through `plug_update_brand` is usually better: the change lands on
the live brand. `plug_create_brand_images(target='brand_document')` hands the file to Plug's own
extractor instead, which lands a DRAFT that a human must review and save in Brand settings, and
nothing about the live kit changes until they do.

## Recipe: brief for an agency or creator partner

1. Map the user's words to this account's tag vocabulary before anything else. "Creator
   content", "UGC", "influencer" and "partner content" are `media_style` values; the account's
   own values come back on any tags read (`tag_name`, `tag_value`). Pass the ones that exist,
   never the nearest-sounding one: an unknown value is refused with the real values listed, and
   the right move is to ask the user which they meant.
2. ONE call: `plug_get_brief_for_peer_group(advertiser_id, cohort_tags={"tags": {"media_style":
   ["Creator content", "UGC"]}}, partner='<who it is for>', ask='double_down' | 'new_angle')`.
   `ask='new_angle'` is for "something new / different / not what we run"; the default briefs
   more of what already wins among those creatives. Never build a brief out of the list tools by hand:
   a brief assembled from four reads is a fifth definition of what Plug already answers once.
3. Show the brief first, then the evidence: `evidence` carries the approach table, the winning
   creatives and the winning and losing elements, each with the population it was measured on.
   Say which creatives the figures cover once, in `population.filters.cohort_description`'s own
   words, and never twice.
4. An empty `briefs` is an answer, not a gap: `lead` says no Plug brief can be used and what was
   searched, `evidence` still carries the reads. Say what they show and write no brief of your
   own. Plug builds a brief from the Creatives data on the Creatives page; one written in a
   message is a proposal no screen shows and the user cannot open, keep or hand on.
5. A creative's Winner or Loser verdict is its peer group's across the account, not a verdict
   among the creatives you narrowed to. Tag-value verdicts ARE measured on those creatives only.
   Say which is which where it matters.
6. Name the filter the way the read names it: say which creatives the figures cover, in the
   sentence `population.filters.cohort_description` comes back with. The word inside that
   field name is ours, not the reader's, and never belongs in a sentence you write.

## Recipe: creative performance review

1. `plug_list_creative_approaches(advertiser_id)`: pass every dimension the user named
   (label, event, funnel, audience, format, period). A figure for a wider population is a
   wrong answer, not an approximation.
2. For any custom date range, use `plug_get_approach_history` (one approach, exact window
   totals) or `plug_list_approaches_in_window` (ranking): do not answer "that window is not
   available".
3. `plug_list_winning_media` / `plug_list_losing_media` for the actual creatives (widest
   window: `period='last_90d'`); `plug_list_winning_tags` / `plug_list_losing_tags` for the
   elements to keep or drop; verdicts are per metric, so pass the metric the user asked about.
   All three families share the defaults in rule 3, so "which media are winning" with nothing
   else named means: the dominant ad account, the last 30 days, active media, the resolved
   event, its largest comparison group, ranked best first against that group's typical ad.
   Say all of that (it is `population.description`), and list the other groups from
   `population.comparison.other_groups` when they hold winners too.
