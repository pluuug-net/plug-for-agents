# Plug for agents

Plug tells you what to create next, grounded in what's working in your paid social on Meta and
TikTok. This repository gives your AI agent Plug's skills and Plug's connector, so it reads
Plug correctly and turns Plug's briefs into finished creatives in your own tools.

## What's inside

| Skill | What it does |
|---|---|
| `plug` | Reads Plug correctly: Moves, creative approaches, winning and losing creatives and elements, briefs, the brand and Plug's documents. |
| `make-creatives` | Makes creatives one step at a time: a static from a Plug brief, short clips from a long video, or a short video from a Plug video brief, finished in your own design, clipping or video tool. |

## Install in Claude (web, desktop, Cowork)

1. Open **Customize > Plugins > Add marketplace** and enter `pluuug-net/plug-for-agents`.
2. Install **Plug**, and turn on **Sync automatically** for this marketplace so you get every
   update.
3. Open the plugin's **Connectors** tab, connect Plug and sign in with your Plug account.
4. Connect the tools your team makes creatives with, for example Canva, OpusClip and
   Replicate.

You need a Plug account with a connected ad account.

## Other agents

The skills in `skills/` follow the [Agent Skills](https://agentskills.io/specification)
format, so agents that read that format can use them as they are. Plug's connector is at
`https://mcp.plug.inc/mcp`.

## Data

The skills store nothing. Plug's connector reads your Plug workspaces at `mcp.plug.inc`, and
changes only your brand settings in Plug, when you ask. It never changes an ad account. The
other tools you connect handle your data under their own terms.

## Changing the skills

- `skills/plug` is a mirror. Its one source is `mcp_server/skill/SKILL.md` in Plug's connector
  (pluuug-net/plug-ai), and a job copies the deployed version from
  `https://mcp.plug.inc/skill.md`. Edit it there, never here.
- `skills/make-creatives` lives here. Every merge to `main` reaches everyone who syncs this
  marketplace, so run the checks in `tests/` before merging.
