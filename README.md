# gocycling — the gocycling.ai plugin for Claude

Plan cycling, gravel and MTB routes on real OpenStreetMap data, in Claude on the web, in Claude
Desktop and in Claude Code.

## Install

Step-by-step instructions: **https://gocycling.ai/claude**

**claude.ai and Claude Desktop**

1. Open **Customize > Plugins**, choose **Add**, then **Add marketplace**, and enter
   `gocycling-ai/plugins`.
2. Install the **gocycling** plugin.
3. On the plugin's **Connectors** tab, add the gocycling connector and connect it. A browser window
   opens to sign in at gocycling.ai, or to create an account there.

**Claude Code**

```
/plugin marketplace add gocycling-ai/plugins
/plugin install gocycling@gocycling
```

The first tool call opens a browser to sign in at gocycling.ai. There is no API key to paste and
nothing to configure: the plugin connects to the server over OAuth.

## What you get

The gocycling.ai routing tools and the route-planning playbook that tells Claude how to use them:
geocode a place, route A→B or a loop, see where the climbing actually is, refine a line, export a
GPX.

Ask for a ride the way you would ask a friend:

> a 60 km gravel loop from Basel, nothing too steep

## How this repository is built

This repository is **generated**, not hand-maintained. It is assembled from the gocycling.ai
application repository by `./gradlew assembleClaudeCodePlugin` and published here whenever the
plugin's version changes. Pull requests here are not merged; the next release overwrites every
file.

It is both the plugin and its marketplace: `.claude-plugin/marketplace.json` lists the one plugin,
which lives at the repository root (`"source": "./"`). The marketplace is named `gocycling`, hence
`gocycling@gocycling` above.

`skills/plan-a-bike-route/SKILL.md` is the same playbook the MCP server serves over
`skill://gocycling/plan-a-bike-route/SKILL.md`. A release is only published once the live server
serves exactly these bytes, so the plugin and the server never tell Claude different things.

The plugin files are MIT-licensed (see `LICENSE`). The gocycling.ai service they connect to is not.
