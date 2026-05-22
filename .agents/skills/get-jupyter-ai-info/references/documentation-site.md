# Documentation Site

Source: https://jupyter-ai.readthedocs.io/en/v3/

## Site Structure

- **Getting Started** — Install, add agents, create a chat, collaborate
- **User Guide** — Chat features, notebook tools, custom MCP servers
  - Troubleshooting
  - Magic commands (optional)
  - Jupyternaut (optional, with Bedrock and vLLM guides)
- **Contributor Guide** — How to contribute
- **Developer Guide** — Entry points API for custom personas

## Installation

```bash
pip install jupyter-ai        # core (no agents included)
# Then install agent(s) of choice:
# Claude: npm install -g @agentclientprotocol/claude-agent-acp
# Codex: npm install -g @zed-industries/codex-acp
# Gemini: install via https://geminicli.com/
# Copilot: npm install -g @github/copilot
# Goose: install via https://github.com/block/goose
# Kiro: install via https://kiro.dev
# Mistral Vibe: uv tool install mistral-vibe
# OpenCode: npm install -g opencode-ai
```

## Key User-Facing Concepts

### Chats
- Chats are `.chat` files saved to disk — resumable, deletable
- Multiple concurrent chats supported (threads)
- Drag-and-drop files or notebook cells as attachments
- `@file:<path>` command for quick file attachment

### AI Personas
- Each agent appears as a persona in chat
- `@`-mention to invoke (e.g., `@Claude How do I...?`)
- Smart reply rules:
  - 1 user + 1 persona → always replies
  - 1 user + N personas → last-mentioned replies
  - N users → must explicitly @-mention

### Notebook Tools
- AI personas can read/write/execute notebooks via `jupyter_server_mcp`
- Create, edit, delete cells; run code through kernel
- Real-time collaboration — other users see agent edits live

### Permissions / Guardrails
- Agents request approval before writing files or running commands
- Read access to workspace is allowed by default

### Custom MCP Servers
- Defined in `.jupyter/mcp_settings.json` at workspace root
- Supports stdio servers (local process) and HTTP servers (remote)
- Available to all ACP agents automatically after restart

### Code Toolbar
- Copy code to clipboard
- Insert as cell above/below active cell
- Replace active cell content
