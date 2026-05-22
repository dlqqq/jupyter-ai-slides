# Subpackages

All required dependencies of the `jupyter_ai` metapackage, plus key optional packages.

## Required Dependencies

| Package | PyPI Name | Purpose |
|---------|-----------|---------|
| jupyterlab_chat | `jupyterlab_chat>=0.21.0` | Chat UI widget for JupyterLab (from `jupyterlab/jupyter-chat`) |
| jupyter_server_documents | `jupyter_server_documents>=0.1.2` | Server-side document handling with kernel management |
| jupyter_ai_router | `jupyter_ai_router>=0.0.3` | Core message routing layer — detects chats, routes to callbacks |
| jupyter_ai_persona_manager | `jupyter_ai_persona_manager>=0.0.8` | Persona registry, lifecycle, entry-point discovery |
| jupyter_ai_chat_commands | `jupyter_ai_chat_commands>=0.0.4` | Default commands: `@file:<path>`, `/refresh-personas` |
| jupyter_ai_acp_client | `jupyter_ai_acp_client>=0.1.0` | ACP client + BaseAcpPersona for wrapping agents |
| jupyter_server_mcp | `jupyter_server_mcp>=0.1.2` | Configurable MCP server extension for Jupyter Server |
| jupyter_ai_tools | `jupyter_ai_tools>=0.4.1` | File, notebook, git, and bash tools for agents |
| jupyterlab_notebook_awareness | `jupyterlab_notebook_awareness>=0.2.0` | Tracks active notebook/cell in collaborative awareness |
| jupyterlab_commands_toolkit | `jupyterlab_commands_toolkit>=0.1.4` | Exposes JupyterLab commands as AI-callable tools |

## Optional Dependencies

| Package | Install Extra | Purpose |
|---------|--------------|---------|
| jupyter_ai_litellm | `jupyter-ai[magics]` or `jupyter-ai[jupyternaut]` | LiteLLM model abstraction |
| jupyter_ai_magic_commands | `jupyter-ai[magics]` | `%%ai` cell magic for inline LLM calls |
| jupyter_ai_jupyternaut | `jupyter-ai[jupyternaut]` | The original Jupyternaut AI persona |

## Other Notable Repos in jupyter-ai-contrib

| Repo | Status | Purpose |
|------|--------|---------|
| jupyter-ai-devrepo | Stable | Monorepo for contributor development (editable installs of all packages) |
| jupyter-ai-claude-code | Experimental | Claude Code persona |
| jupyter-ai-personas | Experimental | Collection of community AI personas |
| jupyter-floating-chat | Experimental | Floating chat input widget |
| jupyterlab-magic-wand | Experimental | In-cell AI assistant |
| jupyterlab-diff | Stable | Cell and file diff commands |
| nb-cli | Experimental | CLI-first interface for AI agents to work with notebooks |
