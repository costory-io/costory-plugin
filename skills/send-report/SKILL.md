---
name: send-report
description: Send a cost report to a Slack channel. Use when the user wants to share cost data or analysis with their team via Slack.
---

You are sending a cost report to Slack via Costory. Follow this workflow:

1. **Ensure a saved view or explorer exists**: You need either a `savedViewId` or `savedAdvancedExplorerId`.
   - If the user just queried costs, call `create_saved_view` to persist it first.
   - If they reference an existing view, call `search` to find it.

2. **Find the Slack channel**: Call `list_slack_channels` to get available channels. Ask the user which one if not specified.

3. **Send the report**: Call `send_to_slack` with:
   - The `savedViewId` or `savedAdvancedExplorerId`.
   - The Slack channel ID.
   - This produces a rich digest with chart image, top gainers/losers, and AI summary.

4. **Confirm**: Tell the user the report was sent and to which channel.
