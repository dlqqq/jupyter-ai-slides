---
name: get-jupyter-ai-info
description: Comprehensive context about Jupyter AI v3.0 for writing presentations, documentation, or discussions. Use when you need facts about Jupyter AI's architecture, features, subpackages, or developer workflow.
---

# Jupyter AI v3.0 — Context Reference

Jupyter AI is an open source JupyterLab extension that connects frontier AI agents to computational notebooks via the Agent Client Protocol (ACP). It provides a native chat UI, real-time notebook tools, a permission system, and extensibility through MCP servers and custom personas.

## References

| Reference | What it covers |
|-----------|---------------|
| [architecture.md](references/architecture.md) | System architecture, layer breakdown, design decisions |
| [subpackages.md](references/subpackages.md) | All subpackages: names, versions, purposes, stability status |
| [features-v3.md](references/features-v3.md) | Headline features of v3.0, what changed from v2 |
| [changelog-v3.md](references/changelog-v3.md) | Release history, breaking changes, contributors |
| [documentation-site.md](references/documentation-site.md) | Synthesized content from readthedocs (user-facing docs) |
| [contributor-guide.md](references/contributor-guide.md) | Developer setup via jupyter-ai-devrepo monorepo |
| [acp.md](references/acp.md) | Agent Client Protocol: installing agents, creating custom personas |
| [mcp.md](references/mcp.md) | MCP servers: adding tools via .jupyter/mcp_settings.json |

## Quick Facts

- **Repo**: https://github.com/jupyterlab/jupyter-ai
- **Docs**: https://jupyter-ai.readthedocs.io/en/v3/
- **Org**: https://github.com/jupyter-ai-contrib
- **Supported agents**: Claude, Codex, Gemini, GitHub Copilot, Goose, Kiro, Mistral Vibe, OpenCode
- **Key protocols**: ACP (agent communication), MCP (tool exposure)
- **v3.0 released**: 2026-03-31
