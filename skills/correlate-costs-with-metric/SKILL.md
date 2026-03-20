---
name: correlate-costs-with-metric
description: Correlate cloud costs with business metrics like DAU, requests/day, or n_clients. Use when the user wants to understand how cost changes relate to business KPIs, check unit economics, or investigate whether a cost spike is driven by growth or inefficiency.
---

You are helping the user correlate cloud costs with business metrics tracked in Costory. This is useful for:

- **Unit economics**: understanding cost-per-user, cost-per-request, or cost-per-client trends over time.
- **Root cause analysis**: determining whether a cost increase is due to business growth (more users, more traffic) or infrastructure inefficiency.
- **Optimization targeting**: identifying services where costs grow faster than the business metrics they support.
- **Reporting**: building context around cost changes by overlaying business KPIs.

## Workflow

1. **Discover available metrics**: Call `list_metrics` to see what business metrics exist for the organization. Each metric has an ID (datasource ID, optionally with `::metricName` suffix) and a name.

2. **Match the user's request** to an available metric. If ambiguous, show the list and ask which metric they'd like to correlate with.

3. **Query both sides**:
   - Call `query_metric` with the chosen metric:
     - `metricId`: the datasource ID from list_metrics (e.g. `datasourceId::metricName`).
     - `from`/`to`: date range. Default to last 3 months if not specified.
     - `aggBy`: aggregation granularity (Day, Week, Month).
   - Call `query_costs` for the same date range and relevant scope to get the cost side of the correlation.

4. **After the queries** (do NOT skip):
   - Call `list_events` for the same date range.
   - Call `suggest_actions` and present follow-up options.

5. **Present the correlation**:
   - Show both the cost trend and the metric trend side by side.
   - Compute unit costs where meaningful (e.g. cost / DAU, cost / requests).
   - Highlight periods where costs and metrics diverge — these are the most actionable insights.
   - Mention correlated events if any.
