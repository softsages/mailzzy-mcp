<p align="center">
  <img src="assets/logo.svg" alt="Mailzzy" height="48">
</p>

# Mailzzy MCP Server

[![Mailzzy MCP connector – tool definition quality and endpoint health on Glama](https://glama.ai/mcp/connectors/com.mailzzy/mcp/badges/score.svg)](https://glama.ai/mcp/connectors/com.mailzzy/mcp)
[![Mailzzy MCP status on mcpi](https://mcpi.app/servers/mailzzy/badge.svg)](https://mcpi.app/servers/mailzzy)

Connect Claude, ChatGPT, Cursor, VS Code and other MCP clients to your Mailzzy account. Ask your
assistant to build an audience, draft a campaign, check it against your sending limits, send a test,
and schedule it, then pull the performance report when it goes out.

This is a **hosted** MCP server. There is nothing to install or run: point your client at the URL
below and sign in with your Mailzzy account.

```
https://api.mailzzy.com/crm/mcp/
```

| | |
| --- | --- |
| Documentation | https://mailzzy.com/docs/#mcp-overview |
| Transport | Streamable HTTP |
| Authentication | OAuth 2.1 with PKCE and dynamic client registration (sign in with Mailzzy) |
| Tools | 49 ([full list](docs/tools.md)) |
| Account needed | Yes, a Mailzzy account ([sign up](https://www.mailzzy.com/)) |
| Registry name | `com.mailzzy/mcp` |

> This repository holds documentation and the registry manifest only. The server itself is
> operated by SoftSages and is not open source.

## What you can do

- **Campaigns**: draft, update, send a test to yourself, send now or schedule, and cancel a
  scheduled campaign.
- **Audiences**: pick groups, segments or tags, see the de-duplicated recipient count, and check it
  against your daily and monthly sending limits before you send.
- **Contacts**: create, update, tag, group, archive, bulk-import from CSV, and export a segment
  or group as CSV.
- **Segments**: build saved filters, preview how many contacts match, then save them.
- **Templates and automations**: create and edit email templates and automation workflows.
- **Transactional email**: send a one-to-one email and read delivery logs.
- **Reports**: campaign metrics, performance over a date range, and per-domain deliverability.

### Example prompts

- "Show me my last five campaigns and their open rates."
- "Create a segment of contacts tagged `webinar-sept` who opened anything in the last 30 days, and
  tell me how many that is."
- "Draft a campaign announcing our October sale to that segment, send me a test, and schedule it for
  Tuesday 10am my time."
- "Which recipient domains are bouncing most this month?"

## Listings

- [Official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=com.mailzzy/mcp) as `com.mailzzy/mcp`
- [Smithery](https://smithery.ai/servers/softsages/mailzzy)
- [Glama](https://glama.ai/mcp/connectors/com.mailzzy/mcp)
- [mcpi](https://mcpi.app/servers/mailzzy) (connection status and client compatibility)

## Connect your client

### Claude (claude.ai, desktop and mobile)

Settings > Connectors > **Add custom connector**, paste `https://api.mailzzy.com/crm/mcp/`, then
**Connect** and sign in.

### Claude Code

```bash
claude mcp add --transport http mailzzy https://api.mailzzy.com/crm/mcp/
```

Then run `/mcp` inside Claude Code and choose **Authenticate**.

### ChatGPT

Settings > Apps and Connectors > Advanced > turn on **Developer mode**, then **Create** a connector
with the URL `https://api.mailzzy.com/crm/mcp/` and authentication **OAuth**.

### Cursor

`~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "mailzzy": {
      "url": "https://api.mailzzy.com/crm/mcp/"
    }
  }
}
```

### VS Code (GitHub Copilot agent mode)

`.vscode/mcp.json`:

```json
{
  "servers": {
    "mailzzy": {
      "type": "http",
      "url": "https://api.mailzzy.com/crm/mcp/"
    }
  }
}
```

### Cline

In the Cline panel open **MCP Servers** > **Configure** > **Remote Servers**, then add:

- **Server Name:** `mailzzy`
- **Server URL:** `https://api.mailzzy.com/crm/mcp/`
- **Transport Type:** Streamable HTTP

Or edit `cline_mcp_settings.json` directly (**Configure** > **Configure MCP Servers**):

```json
{
  "mcpServers": {
    "mailzzy": {
      "type": "streamableHttp",
      "url": "https://api.mailzzy.com/crm/mcp/",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

Sign in with your Mailzzy account when Cline opens the browser. If the server shows an
authentication error, remove it and add it again to restart the sign-in. Setup notes written for
Cline itself are in [llms-install.md](llms-install.md).

### Any other MCP client

Use the URL with Streamable HTTP transport. The server answers unauthenticated requests with
`401` and a `WWW-Authenticate` header pointing at its
[protected resource metadata](https://api.mailzzy.com/core/.well-known/oauth-protected-resource/crm/mcp),
so any client that follows the MCP authorization spec can discover the authorization server and
register itself.

## Authentication and permissions

- You sign in on Mailzzy's own login page. Your password is never shared with the AI client.
- The client receives a short-lived access token scoped to your account. Every tool call acts as
  you and can only see your own account's data.
- Scopes advertised: `mcp:read`, `mcp:write`, `mcp:send`.
- Every tool carries MCP annotations. Read tools are marked read-only. Sending a campaign or
  transactional email, deleting a contact, and cancelling a campaign are marked destructive, so
  well-behaved clients ask you to confirm before running them.
- To disconnect, remove the connector in your client.

## Privacy and security

- Privacy policy: https://www.mailzzy.com/privacy-policy/
- Terms of use: https://www.mailzzy.com/terms-of-use/
- Report a vulnerability: see [SECURITY.md](SECURITY.md)

## Support

- Email: support@mailzzy.com
- Contact page: https://www.mailzzy.com/contact-us/
- Documentation issues with this repository: open a GitHub issue.

---

Mailzzy is a product of [SoftSages](https://www.softsages.com/).
