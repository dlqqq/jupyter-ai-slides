# MCP (Model Context Protocol) in Jupyter AI

Source: https://github.com/jupyter-ai-contrib/jupyter-ai-persona-manager (MCP settings loading)
Source: https://github.com/jupyter-ai-contrib/jupyter-server-mcp (built-in MCP server)

## What is MCP?

The Model Context Protocol is an open standard for giving AI agents access to tools, resources, and prompts. In Jupyter AI, MCP servers provide the tools that agents use to interact with notebooks, files, and external services.

## Built-in MCP Server

Jupyter AI ships with `jupyter_server_mcp` — a configurable MCP server that exposes notebook and file tools to all ACP agents automatically. This is what enables agents to:
- Read/write/execute notebooks
- Manage files
- Run JupyterLab commands

## Adding Custom MCP Servers

Create `.jupyter/mcp_settings.json` at the root of your workspace:

### Stdio Server (local process)

```json
{
  "mcp_servers": [
    {
      "name": "My Custom Tools",
      "command": "npx",
      "args": ["-y", "@my-org/my-mcp-server"],
      "env": [
        {"name": "API_KEY", "value": "sk-abc123"}
      ]
    }
  ]
}
```

### HTTP Server (remote)

```json
{
  "mcp_servers": [
    {
      "type": "http",
      "name": "Remote Tools",
      "url": "https://my-mcp-server.example.com/mcp",
      "headers": [
        {"name": "Authorization", "value": "Bearer my-token"}
      ]
    }
  ]
}
```

### Full Example

```json
{
  "mcp_servers": [
    {
      "name": "Filesystem Tools",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/dir"]
    },
    {
      "name": "GitHub Tools",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": [
        {"name": "GITHUB_PERSONAL_ACCESS_TOKEN", "value": "ghp_xxx"}
      ]
    },
    {
      "type": "http",
      "name": "Company Internal Tools",
      "url": "https://internal-mcp.corp.example.com/mcp",
      "headers": [
        {"name": "Authorization", "value": "Bearer my-token"}
      ]
    }
  ]
}
```

## Schema

### Stdio Server Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `name` | string | yes | Human-readable name |
| `command` | string | yes | Path to MCP server executable |
| `args` | list of strings | yes | Command-line arguments |
| `env` | list of `{name, value}` | no | Environment variables |

### HTTP Server Fields

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `type` | `"http"` | yes | Must be "http" |
| `name` | string | yes | Human-readable name |
| `url` | string | yes | URL to MCP server |
| `headers` | list of `{name, value}` | no | HTTP headers |

## Workflow

1. Create/edit `.jupyter/mcp_settings.json`
2. Restart JupyterLab
3. All configured MCP servers become available to every ACP agent in the session
4. Agents can discover and call tools from these servers (subject to permission system)
