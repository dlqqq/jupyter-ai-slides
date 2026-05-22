# Changelog — Jupyter AI v3.0

Source: https://github.com/jupyterlab/jupyter-ai/blob/main/CHANGELOG.md

## v3.0.0 (2026-03-31)

### What's New
- **Agent support via ACP**: Claude, Codex, Gemini, Goose, Kiro, Mistral Vibe, OpenCode in JupyterLab
- **Real-time chat UI**: Live-streaming responses with tool calls and diff views
- **Tool call permissions**: Agents request approval before writes/executes
- **Jupyter MCP server**: Agents edit and execute notebooks via `jupyter_server_mcp`
- **MCP server integration**: Custom MCP servers via `.jupyter/mcp_settings.json`
- **Multi-chat architecture**: Unlimited chats saved as `.chat` files
- **Complete documentation overhaul**: https://jupyter-ai.readthedocs.io/en/v3/

### Contributors
@dlqqq, @srdas, @Zsailer, @krassowski, @jtpio, @ellisonbg, @3coins

## v3.0.0rc1 (2026-03-25)
- Added `jupyterlab_commands_toolkit` as required dependency

## v3.0.0rc0 (2026-03-25)

First release candidate. Introduced:
- ACP support (Claude, Gemini, Kiro, Mistral Vibe; Codex/OpenCode/Goose WIP)
- Default JupyterLab tools for ACP agents via `jupyter_server_mcp` + `jupyter_ai_tools`
- Custom MCP servers in `.jupyter/mcp_settings.json`

### Breaking Changes from v2
- Jupyternaut no longer required (optional via `pip install 'jupyter-ai[jupyternaut]'`)
- Magic commands no longer included by default (optional via `pip install 'jupyter-ai[magics]'`)
- Package split into modular subpackages under `jupyter-ai-contrib` org
- LangChain-based model providers replaced by ACP agent integration
