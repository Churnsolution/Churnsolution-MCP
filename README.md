# Churn Solution MCP Server

Official [Model Context Protocol](https://modelcontextprotocol.io) server for
[Churn Solution](https://churnsolution.com) — a subscription retention and revenue
recovery platform for B2C subscription businesses on Stripe.

This server gives AI assistants **read-only** access to your Churn Solution retention
data: cancellation-flow metrics, save rates, recovered revenue, offer performance,
cancellation reasons, and customer feedback analytics.

- **Endpoint:** `https://mcp.churnsolution.com`
- **Transport:** Streamable HTTP
- **Auth:** OAuth (you sign in to Churn Solution when connecting)
- **Registry name:** `com.churnsolution/analytics`
- **Docs:** https://churnsolution.com/docs/mcp-server

## Tools

| Tool | Purpose |
|---|---|
| `get_cancel_flow_metrics` | Overall cancellation-flow performance metrics |
| `get_cancel_flow_outcomes_by_flow` | Outcomes broken down by individual flow |
| `get_cancel_flow_revenue` | Revenue retained/recovered through cancel flows |
| `get_cancel_flow_revenue_by_offer` | Recovered revenue attributed to each save offer |
| `get_cancel_flow_save_rate` | Save rate (share of cancellations prevented) |
| `list_cancel_flow_cancellation_reasons` | Cancellation reasons across all sessions |
| `list_cancel_flow_cancellation_reasons_by_plan` | Cancellation reasons segmented by plan |
| `list_cancel_flow_offer_performance` | Performance of each save offer |
| `list_connections` | Connected billing/data integrations |
| `list_plans` | Subscription plans |
| `search_cancel_flow_sessions` | Search individual cancellation sessions |
| `get_feedback_category_breakdown` | Customer feedback grouped by category |
| `get_feedback_sentiment_trend` | Sentiment trend over time |
| `list_feedback_intents` | Detected feedback intents |

## Connecting

### Cursor
```json
{
  "mcpServers": {
    "churnsolution": {
      "url": "https://mcp.churnsolution.com"
    }
  }
}
```

### VS Code
```json
{
  "servers": {
    "churnsolution": {
      "type": "http",
      "url": "https://mcp.churnsolution.com"
    }
  }
}
```

### Claude / ChatGPT
Add a custom connector pointing to `https://mcp.churnsolution.com` and set the
authentication mode to **OAuth**, then sign in to Churn Solution.

Full setup guide: https://churnsolution.com/docs/mcp-server

## About Churn Solution

Churn Solution reduces cancellations, recovers failed payments, and wins back churned
subscribers for B2C subscription businesses on Stripe. Learn more at
[churnsolution.com](https://churnsolution.com).
