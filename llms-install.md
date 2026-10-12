# Installing the Mailzzy MCP server (instructions for AI assistants)

Mailzzy is a **hosted, remote** MCP server. There is nothing to clone, build, install or run, and
no API key or environment variable. Setup is one config entry plus a browser sign-in by the user.

## Do not

- Do not run `npm`, `npx`, `pip`, `uvx`, `docker` or `git clone`. This repository contains
  documentation only; there is no package and no local process.
- Do not ask the user for an API key, token, password or tenant ID. Authentication is OAuth in
  the browser.
- Do not remove the trailing slash from the URL. Without it the client cannot connect.

## Steps

1. Add this entry to the MCP settings file (`cline_mcp_settings.json`), keeping any servers that
   are already there:

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

2. Tell the user a browser window will open and they should sign in with their Mailzzy account
   and approve access. If they do not have an account, they can create one at https://mailzzy.com.
3. If no browser window opens, or the server reports an authentication error, ask the user to
   authorize it from the MCP Servers panel, or remove the server and add it again to restart the
   sign-in.

## Verify

After sign-in the server should list 49 tools. A safe read-only check is to call
`mcp_crm_campaigns_list` (for example, the user asking: "Show me my last five campaigns and their open rates."). Do not call tools that send email or
delete data to test the connection.

## Details

| | |
| --- | --- |
| URL | `https://api.mailzzy.com/crm/mcp/` |
| Transport | Streamable HTTP |
| Authentication | OAuth 2.1 with PKCE and dynamic client registration (no client ID or secret to configure) |
| Tools | 49, listed in [docs/tools.md](docs/tools.md) |
| Docs | https://mailzzy.com/docs/#mcp-overview |
| Support | support@mailzzy.com |
