<p align="center">
  <img src="./icon-512.png" alt="Competitor Tracker & Co." width="120" height="120">
</p>

# Competitor Tracker MCP server

[![smithery badge](https://smithery.ai/badge/competitortracker/competitortracker)](https://smithery.ai/servers/competitortracker/competitortracker)

Track your competitors from inside your AI assistant. This is the remote [Model Context Protocol](https://modelcontextprotocol.io) server for **Competitor Tracker & Co.** Subscribe to competitors, read their change feed, and pull page snapshots straight from Claude, Cursor, ChatGPT, or any other MCP client. No browser tab required.

- **Website:** https://competitortracker.io
- **Docs:** https://competitortracker.io/docs/mcp/
- **Demo:** https://competitortracker.io/demo/agent/
- **MCP endpoint:** `https://mcp.competitortracker.io/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth (sign in on first tool call) or an `X-API-Key` header

![Claude calling the Competitor Tracker MCP server to summarise this week's competitor changes across pricing, product and messaging](https://competitortracker.io/img/mcp/competitor-tracker-mcp-weekly-changes.png)

## See it in action

Not ready to connect? Watch [the agent desk](https://competitortracker.io/demo/agent/): a recorded Claude session on this MCP server, working a live case of 25 competitive-intelligence rivals from April to July. Real tool calls, real detected changes. The [same case as a Monday email brief](https://competitortracker.io/demo/human/) sits next door, and the [demo hub](https://competitortracker.io/demo/) shows both.

![Claude using the Competitor Tracker MCP server to build a payroll-industry pricing radar report from tracked competitor data](https://competitortracker.io/img/mcp/competitor-tracker-mcp-pricing-radar.png)

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

The server exposes ~50 tools. Read tools need no special scope; `(write)` tools change your workspace and `(destructive)` tools require an explicit `confirm: true`.

- `list_competitors`: list the competitors your organization tracks
- `get_competitor`: fetch one competitor's details, categories and labels
- `get_competitor_timeline`: chronological activity for a competitor
- `list_pages`: list tracked pages, optionally filtered by type
- `get_snapshot`: retrieve a snapshot with HTML, markdown and screenshot assets
- `list_snapshots`: list snapshots for a tracked page
- `list_org_changes`: read the organization-wide change feed with filters
- `list_competitor_changes`: changes for a single competitor
- `list_snapshot_changes`: changes attributed to a specific snapshot
- `list_labels`: the organization's labels with colors
- `get_label`: a single label's details
- `get_current_user`: the signed-in user's profile
- `list_my_orgs`: organizations the user belongs to
- `get_balance`: coin balance and renewal summary
- `list_transactions`: coin transaction history
- `get_org`: current organization details
- `list_members`: active organization members
- `list_invites`: pending invitations
- `list_api_keys`: API keys with metadata, secrets excluded
- `list_api_key_usage`: API key usage logs
- `list_dispatches`: the organization's notifications
- `list_dispatch_deliveries`: email delivery attempts
- `list_webhooks`: registered webhooks
- `list_webhook_deliveries`: webhook delivery attempts
- `subscribe_competitor`: start tracking a competitor by URL (write)
- `update_competitor`: change display name or tracked categories (write)
- `create_label`: add a new label (write)
- `update_label`: rename or recolor a label (write)
- `assign_label`: apply a label to a competitor (write)
- `update_current_user`: update profile name fields (write)
- `update_org`: rename the organization, admin only (write)
- `update_member_role`: change a member's permissions (write)
- `create_invite`: invite a new member by email (write)
- `mint_api_key`: generate a new API key with scopes (write)
- `create_dispatch`: create a notification with optional label scoping (write)
- `update_dispatch`: modify notification settings (write)
- `add_dispatch_recipient`: add a recipient to a notification (write)
- `create_webhook`: register a webhook endpoint (write)
- `list_pages`: list tracked pages, optionally filtered by type
- `get_snapshot`: retrieve a snapshot with HTML, markdown and screenshot assets
- `list_snapshots`: list snapshots for a tracked page
- `list_org_changes`: read the organization-wide change feed with filters
- `list_competitor_changes`: changes for a single competitor
- `list_snapshot_changes`: changes attributed to a specific snapshot
- `list_labels`: the organization's labels with colors
- `get_label`: a single label's details
- `get_current_user`: the signed-in user's profile
- `list_my_orgs`: organizations the user belongs to
- `get_balance`: coin balance and renewal summary
- `list_transactions`: coin transaction history
- `get_org`: current organization details
- `list_members`: active organization members
- `list_invites`: pending invitations
- `list_api_keys`: API keys with metadata, secrets excluded
- `list_api_key_usage`: API key usage logs
- `list_dispatches`: the organization's notifications
- `list_dispatch_deliveries`: email delivery attempts
- `list_webhooks`: registered webhooks
- `list_webhook_deliveries`: webhook delivery attempts
- `subscribe_competitor`: start tracking a competitor by URL (write)
- `update_competitor`: change display name or tracked categories (write)
- `create_label`: add a new label (write)
- `update_label`: rename or recolor a label (write)
- `assign_label`: apply a label to a competitor (write)
- `update_current_user`: update profile name fields (write)
- `update_org`: rename the organization, admin only (write)
- `update_member_role`: change a member's permissions (write)
- `create_invite`: invite a new member by email (write)
- `mint_api_key`: generate a new API key with scopes (write)
- `create_dispatch`: create a notification with optional label scoping (write)
- `update_dispatch`: modify notification settings (write)
- `add_dispatch_recipient`: add a recipient to a notification (write)
- `create_webhook`: register a webhook endpoint (write)
- `unsubscribe_competitor`: stop tracking a competitor (destructive)
- `delete_label`: remove a label from all competitors (destructive)
- `unassign_label`: detach a label from a competitor (destructive)
- `delete_org`: delete the organization, owner only (destructive)
- `transfer_org_ownership`: change the owner (destructive)
- `leave_org`: exit the organization (destructive)
- `revoke_invite`: cancel a pending invitation (destructive)
- `revoke_api_key`: disable an API key permanently (destructive)
- `regenerate_api_key`: rotate an API key secret (destructive)
- `delete_dispatch`: remove a notification (destructive)
- `remove_dispatch_recipient`: unsubscribe a notification recipient (destructive)
- `delete_webhook`: delete a webhook registration (destructive)

The full, always-current catalogue is at [competitortracker.io/docs/mcp/tools](https://competitortracker.io/docs/mcp/tools/).

## Who it's for

Founders, product and marketing teams who already live in an AI assistant and want competitor intelligence where they work: pricing moves, page changes, launches. Not in yet another dashboard.

## About this repository

This repo is the **public listing and manifest** for the Competitor Tracker MCP server (`server.json`, client config, install notes). The server itself runs remotely at `https://mcp.competitortracker.io/mcp`, so there is nothing to build or host here. To use it, just point your client at the endpoint.

## License

[MIT](./LICENSE).
