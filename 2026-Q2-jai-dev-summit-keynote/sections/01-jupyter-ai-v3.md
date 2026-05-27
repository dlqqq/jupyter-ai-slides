---
layout: section
_meta:
  duration: 20min
  outline:
    - Jupyter AI v3.0 launch
    - New documentation page
    - ACP and supported agents
    - Notebook native tools
    - Multiple chats and personas
    - MCP servers
    - Guardrails
    - Architecture overview
---

# Jupyter AI v3.0

---

# We shipped! 🎉

**Jupyter AI v3.0** — released March 30, 2026

<v-clicks>

- **Frontier agents via ACP** — Claude, Codex, Gemini, Copilot, Goose, Kiro, Mistral Vibe, OpenCode
- **Notebook native tools** — agents edit and run notebooks in real time
- **Multiple chats** — unlimited threads, saved as `.chat` files
- **AI Personas** — @-mention any agent, build your own
- **Custom MCP servers** — extend agents with domain-specific tools
- **Guardrails by default** — permission system for writes and executes

</v-clicks>

---

# New documentation page


- Check it out! https://jupyter-ai.readthedocs.io
- Modernized landing page and style
- Refreshed documentation
- New "Getting Started" guide on how to install new agents

---

# The v3.0 experience

Feel free to try it out live! `pip install jupyter-ai`

<v-click>

**Chats are files** — create, resume, delete like any document.

</v-click>

<v-click>

**Personas** — each agent is an @-mentionable persona:

- `@Claude How do I parallelize this?`
- `@Gemini Explain this error`

</v-click>

<v-click>

- Permission requests show up in the chat with accompanying diffs (thank you Andrii!)

- Tool call results immediately visible in JupyterLab

</v-click>

---

# Agent Client Protocol (ACP)

Bring your own agent

<v-click>

**What ACP does**: Gives us a unified method to invoke agents, render rich UIs, return permission controls, and provide a toolkit out-of-the-box

</v-click>

<v-click>

**Supported agents:**

Claude · Codex · Gemini · GitHub Copilot · Goose · Kiro · Mistral Vibe · OpenCode

</v-click>

<v-click>

**How it works:**

</v-click>

<v-clicks depth=99>

- Install an agent → it's auto-detected
- Start JupyterLab and it's there, ready to help
- Agents run as external processes
- No vendor lock-in
- See the "Getting Started" guide (and feel free to play with it!)

</v-clicks>

---

# Notebook Native Tools

Agents can **read, write, and execute** notebooks in real time.

- Powered by `jupyter_server_mcp` + `jupyter_ai_tools`
- Other users see agent edits live (RTC)
- Tools: read/write cells, run code, create notebooks, and open + run them for you

<!-- TODO: screenshot or demo video of agent editing a notebook -->

---

# Custom MCP Servers

Extend agent capabilities with `.jupyter/mcp_settings.json`:

```json
{
  "mcp_servers": [
    {
      "name": "GitHub Tools",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": [{"name": "GITHUB_PERSONAL_ACCESS_TOKEN", "value": "ghp_..."}]
    }
  ]
}
```

<v-click>

Supports **stdio** (local) and **HTTP** (remote) servers.

All ACP agents get access automatically (after you restart JupyterLab).

</v-click>

---

# Major RTC performance and reliability improvements

`jupyter_server_documents` v0.2.0

<v-clicks depth=99>

- Instant UI refresh on file changes (PR #202)
  - Thanks Sathish from Apple!
- Automatic memory management (PR #193)
  - Fix made upstream in `pycrdt`
- Fixed the notorious RTC content duplication bug that has existed for years (PR #215)
  - Fix has since been ported to `jupyter_collaboration`

</v-clicks>