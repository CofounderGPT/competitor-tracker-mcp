# Installing the Competitor Tracker MCP server

This is a **remote** MCP server. There is no package to install and nothing to run locally — you only need to register the endpoint with an MCP client.

- **Endpoint:** `https://mcp.competitortracker.io/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth on first tool call, or an `X-API-Key` header for headless use.

## Register the server

Pick the block for the client you are configuring.

**Claude (CLI):**

```sh
claude mcp add --transport http competitor-tracker https://mcp.competitortracker.io/mcp
```

**Cursor** — `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "competitor-tracker": {
      "url": "https://mcp.competitortracker.io/mcp"
    }
  }
}
```

**Windsurf** — `~/.codeium/windsurf/mcp_config.json`:

```json
{
  "mcpServers": {
    "competitor-tracker": {
      "serverUrl": "https://mcp.competitortracker.io/mcp"
    }
  }
}
```

**Cline** — MCP settings:

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

After registering, trigger any tool (e.g. `list_competitors`) to start the OAuth sign-in. For automated environments, set an `X-API-Key` header with a key generated at https://competitortracker.io/docs/api-keys/.

Full docs: https://competitortracker.io/docs/mcp/connect/
