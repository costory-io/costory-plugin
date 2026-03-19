# Costory Plugin for Claude Code

Cloud cost management tools for AWS, GCP, and Azure — powered by [Costory](https://costory.io).

## Installation

```bash
/plugin marketplace add costory-io/costory-plugin
/plugin install costory@costory-marketplace
```

## Setup

After installing, run `/mcp` in Claude Code and follow the browser OAuth flow to log in with your Costory account.

## Skills

| Skill | Description |
|-------|-------------|
| `/costory:analyze-costs` | Analyze cloud costs by service, team, environment, or any dimension |
| `/costory:investigate-change` | Investigate cost spikes and compare periods |
| `/costory:query-metric` | Query custom business metrics (DAU, requests/day, etc.) |
| `/costory:setup-alert` | Create cost alerts with Slack notifications |
| `/costory:send-report` | Send cost reports to Slack channels |

## Agents

| Agent | Description |
|-------|-------------|
| `cost-investigator` | Autonomous deep-dive investigation — drills down across dimensions to find root causes of cost changes |

## MCP Tools

The plugin connects to the Costory MCP server which provides:

- `search` — discover dimensions, dashboards, views, events, metrics
- `query_costs` — query cost data grouped by dimensions
- `query_metric` — query custom business metrics
- `list_metrics` — list available metric datasources
- `get_cost_diff` — compare costs between periods
- `get` — fetch dashboard/view/explorer configs
- `suggest_groupby` — find the best dimension to split by
- `list_events` — correlate cost changes with events
- `create_event` — annotate cost changes
- `create_saved_view` — persist queries as reusable views
- `create_alert` — set up cost alerts
- `list_alerts` — view existing alerts
- `list_slack_channels` — discover Slack channels
- `send_to_slack` — send rich cost reports to Slack
- `suggest_actions` — get context-aware follow-up suggestions
- `list_organizations` — list accessible organizations
