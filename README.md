# Flowhawk for coding agents

Production data from [Flowhawk](https://flowhawk.dev) inside Claude Code and Cursor: incidents, errors, traces and logs, organised by the business flow they hit. The plugin connects your agent to your workspace's MCP server and adds four skills.

| Skill | What it does |
| --- | --- |
| `investigate-incident` | From an incident to the failing step, what changed, what was ruled out, and the code in this repository |
| `fix-issue` | From an error (ERR-12) to its cause in the code, a fix and a test |
| `check-release` | Whether a deploy moved a flow or brought new errors |
| `set-up-flowhawk` | Adds the SDK and the business flows to this repository (run it yourself, the agent won't start it on its own) |

## Install

**Claude Code**

```
/plugin marketplace add flowhawk-dev/flowhawk-plugin
/plugin install flowhawk@flowhawk
```

Then run `/mcp`, choose `flowhawk` and sign in. You act with your own role: viewers read, editors can also propose changes. Skills run as `/flowhawk:investigate-incident`, `/flowhawk:fix-issue 12` and so on, and the agent picks them up on its own when you describe the task.

**Cursor**

Copy this repository into `~/.cursor/plugins/local/flowhawk` and reload the window, or add it as a team marketplace under Dashboard > Plugins & MCPs. Sign in to the `flowhawk` MCP server when Cursor asks.

**Another workspace address**

The plugin points at `https://api.flowhawk.dev/mcp`. If you run Flowhawk in your own cloud, change the address in `.mcp.json` and `mcp.json` to your API's `/mcp`.

## What the agent can and can't do

Everything goes through your workspace's MCP server, under your role, and every tool call is in the audit log under your name. Config changes are proposed as a diff you confirm. The skills tell the agent to treat telemetry as data, and not to deploy, roll back or resolve anything unless you ask.

## Privacy

The plugin sends nothing by itself. Your agent talks to your Flowhawk workspace over MCP, under the [privacy policy](https://flowhawk.dev/privacy.html).

## Licence

Apache-2.0.
