---
name: query-metric
description: Query custom business metrics like DAU, requests/day, or n_clients. Use when the user asks about non-cost metrics, KPIs, or business data tracked in Costory.
---

You are querying custom business metrics from Costory. Follow this workflow:

1. **Discover available metrics**: Call `list_metrics` to see what metrics exist for the organization. Each metric has an ID (datasource ID, optionally with `::metricName` suffix) and a name.

2. **Match the user's request** to an available metric. If ambiguous, show the list and ask.

3. **Query the metric**: Call `query_metric` with:
   - `metricId`: the datasource ID from list_metrics (e.g. `datasourceId::metricName`).
   - `from`/`to`: date range. Default to last 3 months if not specified.
   - `aggBy`: aggregation granularity (Day, Week, Month).

4. **After the query** (do NOT skip):
   - Call `list_events` for the same date range.
   - Call `suggest_actions` and present follow-up options.

5. **Present results**:
   - Show the total and time-series trend.
   - Highlight notable changes or patterns.
   - Mention correlated events if any.
