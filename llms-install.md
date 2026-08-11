# Installation guide for AI assistants

This guide is for AI coding assistants (Cline, Cursor, and similar) setting up the
Churn Solution MCP server on a user's behalf.

## Important: this is a remote server

There is **nothing to install, clone, build, or run locally** — no npm package, no Docker
image, no Python environment. Churn Solution is a hosted MCP server. Setup is a single
configuration entry pointing at the public endpoint.

- **URL:** `https://mcp.churnsolution.com`
- **Transport:** Streamable HTTP
- **Authentication:** OAuth — the user signs in to Churn Solution in a browser on first
  connect. **Do not** ask the user for an API key, token, or secret; none exists and none
  is required.
- **Prerequisite:** the user needs a Churn Solution account (https://churnsolution.com).

## Cline

Add the following to `cline_mcp_settings.json` under `mcpServers`:

```json
{
  "mcpServers": {
    "churnsolution": {
      "type": "streamableHttp",
      "url": "https://mcp.churnsolution.com",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

**`"type": "streamableHttp"` is required** (camelCase). If it is omitted, Cline falls back
to the legacy SSE transport and the connection will fail.

Save the file — Cline connects automatically. On first use the user completes an OAuth
sign-in in the browser.

## Cursor

```json
{
  "mcpServers": {
    "churnsolution": {
      "url": "https://mcp.churnsolution.com"
    }
  }
}
```

## VS Code

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

## Verifying the setup

List the available tools. A working connection exposes read-only tools including
`get_cancel_flow_metrics`, `get_cancel_flow_save_rate`, `get_cancel_flow_revenue`,
`list_plans`, and `list_connections`.

A good first call is `list_plans` — it requires no arguments and confirms both the
connection and the OAuth session.

## Troubleshooting

| Symptom | Cause / fix |
|---|---|
| Connection fails immediately | `"type": "streamableHttp"` missing — Cline defaulted to SSE. Add it. |
| Prompted for an API key | Misconfiguration; this server uses OAuth only. Remove any `headers` block. |
| Tools list is empty | OAuth sign-in not completed — trigger a tool call to start the browser flow. |
| 401 / unauthorized | The signed-in account has no Churn Solution access. Sign in with the account that owns the data. |

Full documentation: https://churnsolution.com/docs/mcp-server
