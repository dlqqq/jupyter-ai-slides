# Architecture

Jupyter AI is a metapackage (`jupyter_ai`) that composes ~10 subpackages into a unified AI experience for JupyterLab. The metapackage lives at `jupyterlab/jupyter-ai`; all subpackages live under the `jupyter-ai-contrib` GitHub org.

## High-Level Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    JupyterLab (frontend)                 │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │ Chat UI      │  │ Notebook     │  │ Commands     │  │
│  │ (jupyterlab- │  │ Awareness    │  │ Toolkit      │  │
│  │  chat)       │  │              │  │              │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
                          │
┌─────────────────────────────────────────────────────────┐
│                 Jupyter Server (backend)                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │ Router       │  │ Persona      │  │ ACP Client   │  │
│  │              │  │ Manager      │  │              │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  │
│  │ Server MCP   │  │ AI Tools     │  │ Server Docs  │  │
│  │              │  │              │  │              │  │
│  └──────────────┘  └──────────────┘  └──────────────┘  │
└─────────────────────────────────────────────────────────┘
                          │
┌─────────────────────────────────────────────────────────┐
│              External ACP Agent Processes                 │
│  Claude │ Codex │ Gemini │ Copilot │ Goose │ Kiro │ ...│
└─────────────────────────────────────────────────────────┘
```

## Layer Breakdown

### Frontend Layer
- **jupyterlab_chat** — Chat UI widget (from `jupyterlab/jupyter-chat` repo)
- **jupyterlab-notebook-awareness** — Tracks active notebook/cell per user for collaborative awareness
- **jupyterlab-commands-toolkit** — Exposes JupyterLab commands as AI-callable tools

### Routing & Messaging Layer
- **jupyter_ai_router** — Core message routing: detects new chats, routes messages to callbacks (slash commands vs regular messages)
- **jupyter_ai_chat_commands** — Default chat commands (`@file:<path>`, `/refresh-personas`)

### Persona Layer
- **jupyter_ai_persona_manager** — Registry and lifecycle for AI personas; entry-point discovery; loads personas from `.jupyter/personas/`
- **jupyter_ai_acp_client** — ACP client implementation + `BaseAcpPersona` base class for wrapping ACP agents as personas

### Tool Layer
- **jupyter_server_mcp** — Configurable MCP server extension; registers Python functions as tools; provides stdio proxy for external clients
- **jupyter_ai_tools** — File system, notebook, git, and bash tools for agents
- **jupyter_server_documents** — Server-side document handling with kernel management

### Optional
- **jupyter_ai_jupyternaut** — The original Jupyternaut persona (now optional)
- **jupyter_ai_litellm** — LiteLLM model abstraction
- **jupyter_ai_magic_commands** — `%%ai` cell magic (now optional)

## Key Design Decisions

1. **ACP over custom agents** — v3 delegates agent logic to external processes via ACP rather than building/maintaining agents internally
2. **MCP for tools** — Tools are exposed via MCP, making them available to any MCP-compatible client
3. **Entry points for extensibility** — Personas and tools are discovered via Python entry points, enabling pip-installable extensions
4. **Chats as files** — `.chat` files persist conversation history and can be resumed
5. **Permission system** — Agents must request approval before writes/executes (guardrails by default)
