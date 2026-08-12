# Security Policy

## Reporting a vulnerability

Please report security issues **privately** — do not open a public issue.

Use [GitHub Security Advisories](https://github.com/Churnsolution/Churnsolution-MCP/security/advisories/new)
to report privately, or contact us through https://churnsolution.com.

We aim to acknowledge reports within 3 business days.

## Security model

The Churn Solution MCP server is a hosted, remote server. This repository contains
documentation and configuration only — no server code and no credentials.

- **Transport:** HTTPS only (streamable HTTP) at `https://mcp.churnsolution.com`.
- **Authentication:** OAuth. No API keys, tokens, or secrets are stored in client
  configuration, and none should ever be committed to a repository or shared.
- **Authorization:** each user sees only the Churn Solution data their own account can
  access. The MCP session is scoped to the authenticated user.
- **Access level:** all exposed tools are **read-only**. The server exposes no tool that
  creates, modifies, or deletes data, and none that initiates payments or refunds.
- **Data handling:** the server returns your own subscription and retention data. Treat
  tool output as confidential business data, and be aware that connecting any MCP client
  means that client (and its model provider) will process the data returned.

## Scope

Vulnerabilities in the hosted service at `mcp.churnsolution.com` and in the configuration
guidance in this repository are both in scope.
