---
name: setup-alert
description: Create a cost alert that monitors a query and notifies via Slack when thresholds are exceeded. Use when the user wants to be alerted about cost changes.
---

You are setting up a cost alert in Costory. Follow this workflow:

1. **Understand what to monitor**: Ask the user what they want to alert on if not clear (e.g. "Alert me if EC2 costs exceed $10k/month").

2. **Create a saved view first**: Call `create_saved_view` with the query configuration (groupBy, filters, date range) that captures what to monitor. Note the returned savedViewId.

3. **Find Slack channels**: Call `list_slack_channels` to discover available channels for notifications.

4. **Create the alert**: Call `create_alert` with:
   - The `savedViewId` from step 2.
   - Threshold configuration.
   - Slack channel IDs for notifications.

5. **Present the result**: Include the alert URL so the user can view and edit it in the Costory UI.
