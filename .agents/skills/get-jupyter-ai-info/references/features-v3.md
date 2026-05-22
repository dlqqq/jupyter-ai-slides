# Features — Jupyter AI v3.0

## Headline Features

### 1. Agent Support via ACP (Agent Client Protocol)
- Frontier coding agents run as external processes, connected via ACP
- Supported agents: Claude, Codex, Gemini, GitHub Copilot, Goose, Kiro, Mistral Vibe, OpenCode
- Agents are auto-detected when their dependencies are installed
- No vendor lock-in — ACP is an open standard (like LSP for language servers)

### 2. Notebook Native Tools
- Agents can read, write, and execute notebooks in real time
- Powered by `jupyter_server_mcp` + `jupyter_ai_tools`
- Tools: read_notebook, read_cell, add_cell, edit_cell, delete_cell, create_notebook
- Other users see agent edits live via RTC (real-time collaboration)

### 3. Multiple Concurrent Chats
- Chats are `.chat` files — create unlimited threads
- Resume by re-opening the file
- Each chat is independent with its own history

### 4. AI Personas
- Each agent appears as a named persona (e.g., @Claude, @Gemini)
- @-mention to invoke, just like mentioning a human
- Custom personas via Python entry points or `.jupyter/personas/` directory
- Personas have avatars, descriptions, and system prompts

### 5. Custom MCP Servers
- Add domain-specific tools via `.jupyter/mcp_settings.json`
- Supports stdio (local) and HTTP (remote) MCP servers
- All ACP agents automatically get access to configured MCP tools

### 6. Permission System (Guardrails)
- Agents request approval before writing files or running commands
- Read access allowed by default
- Tool call permissions shown in chat UI

### 7. Real-Time Chat UI
- Live-streaming responses with tool call status
- Reasoning traces and execution plans visible
- Inline diff views for file edits
- Drag-and-drop attachments (files, notebook cells)

## What Changed from v2

| v2 | v3 |
|----|-----|
| Jupyternaut was the only AI persona (required) | Jupyternaut is optional; frontier agents via ACP |
| Single chat | Multiple concurrent chats |
| Magic commands included by default | Magic commands optional (`jupyter-ai[magics]`) |
| Custom model providers via LangChain | ACP agents + MCP tools (open standards) |
| Monolithic package | Modular subpackages under jupyter-ai-contrib |

## Why ACP?

Rather than building/maintaining its own agent, Jupyter AI v3 focuses on integration. ACP standardizes how editors connect to coding agents — the same way LSP standardized language servers. By adopting ACP, JupyterLab joins Zed, JetBrains, VS Code, and Neovim as a first-class ACP client.
