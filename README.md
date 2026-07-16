<p align="center">
  <img src="./icon-512.png" alt="Competitor Tracker & Co." width="120" height="120">
</p>

# Competitor Tracker MCP server

[![smithery badge](https://smithery.ai/badge/competitortracker/competitortracker)](https://smithery.ai/servers/competitortracker/competitortracker)ó

Track your competitors from inside your AI assistant. This is the remote [Model Context Protocol](https://modelcontextprotocol.io) server for **Competitor Tracker & Co.** Subscribe to competitors, read their change feed, and pull page snapshots straight from Claude, Cursor, ChatGPT, or any other MCP client. No browser tab required.

- **Website:** https://competitortracker.io
- **Docs:** https://competitortracker.io/docs/mcp/
- **Demo:** https://competitortracker.io/demo/agent/
- **MCP endpoint:** `https://mcp.competitortracker.io/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth (sign in on first tool call) or an `X-API-Key` header

## See it in action

Not ready to connect? Watch [the agent desk](https://competitortracker.io/demo/agent/): a recorded Claude session on this MCP server, working a live case of 25 competitive-intelligence rivals from April to July. Real tool calls, real detected changes. The [same case as a Monday email brief](https://competitortracker.io/demo/human/) sits next door, and the [demo hub](https://competitortracker.io/demo/) shows both.

## Connecting

Point any MCP-compatible client at the endpoint above.

### Claude

```sh
claude mcp add --transport http competitor-tracker https://mcp.competitortracker.io/mcp
```

### Cursor

Add to `~/.cursor/mcp.json`, then enable it in **Settings → MCP**:

```json
{
  "mcpServers": {
    "competitor-tracker": {
      "url": "https://mcp.competitortracker.io/mcp"
    }
  }
}
```

### ChatGPT

**Settings → Connectors → Add custom connector**, using the endpoint URL above.

### Windsurf

Add to `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "competitor-tracker": {
      "serverUrl": "https://mcp.competitortracker.io/mcp"
    }
  }
}
```

### Cline

```json
{
  "mcpServers": {
    "competitor-tracker": {
      "type": "streamableHttp",
      "url": "https://mcp.competitortracker.io/mcp"
    }
  }
}
```

### Raycast

Add a remote MCP server from **AI → MCP Servers**, using the endpoint URL above.

Full per-client instructions live at [competitortracker.io/docs/mcp/connect](https://competitortracker.io/docs/mcp/connect/).

## Authentication

On the first tool call the server walks you through an OAuth sign-in. For headless or automated use, generate an API key in the app and send it as an `X-API-Key` header. See [API keys](https://competitortracker.io/docs/api-keys/).

## Tools

The server exposes ~50 tools across the workspace. A sample:

| Tool | What it does |
| --- | --- |
| `list_competitors` | List the competitors your organization tracks |
| `subscribe_competitor` | Start tracking a competitor by URL |
| `list_org_changes` | Read the organization-wide change feed, with filters |
| `get_competitor_timeline` | Chronological activity for one competitor |
| `list_snapshots` / `get_snapshot` | Tracked-page snapshots with HTML, markdown and screenshots |
| `list_labels` / `assign_label` | Organize competitors with labels |
| `create_dispatch` | Set up a notification / weekly dossier |
| `create_webhook` | Register a webhook endpoint for changes |

Read tools need no special scope; **write** tools modify your workspace and **destructive** tools require an explicit `confirm: true`. The complete, always-current catalogue is at [competitortracker.io/docs/mcp/tools](https://competitortracker.io/docs/mcp/tools/).

## Who it's for

Founders, product and marketing teams who already live in an AI assistant and want competitor intelligence where they work: pricing moves, page changes, launches. Not in yet another dashboard.

## About this repository

This repo is the **public listing and manifest** for the Competitor Tracker MCP server (`server.json`, client config, install notes). The server itself runs remotely at `https://mcp.competitortracker.io/mcp`, so there is nothing to build or host here. To use it, just point your client at the endpoint.

## License

[MIT](./LICENSE).
