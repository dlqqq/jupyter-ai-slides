# ACP (Agent Client Protocol)

Source: https://github.com/jupyter-ai-contrib/jupyter-ai-acp-client

## What is ACP?

The Agent Client Protocol is an open standard for connecting coding agents to editors — analogous to LSP for language servers. By adopting ACP, JupyterLab joins Zed, JetBrains, VS Code, and Neovim as a first-class ACP client.

## How It Works in Jupyter AI

1. The `jupyter_ai_acp_client` package provides `BaseAcpPersona` — a base class for wrapping any ACP agent as a Jupyter AI persona
2. Each persona spawns the agent as a subprocess and communicates via ACP
3. The ACP client provides `prompt_and_reply()` which streams responses back to chat
4. Agents get file read/write and terminal capabilities through the ACP client

## Installing an ACP Agent

Each agent requires its own CLI tool plus (sometimes) an ACP adapter:

| Agent | Install CLI | Install ACP Adapter |
|-------|-------------|---------------------|
| Claude | [docs.anthropic.com](https://docs.anthropic.com/en/docs/claude-code/quickstart) | `npm install -g @agentclientprotocol/claude-agent-acp` |
| Codex | [developers.openai.com](https://developers.openai.com/codex/cli) | `npm install -g @zed-industries/codex-acp` |
| Gemini | [geminicli.com](https://geminicli.com/) | Built-in (>= 0.34.0) |
| Copilot | [GitHub docs](https://docs.github.com/en/copilot/how-tos/copilot-cli/set-up-copilot-cli/install-copilot-cli) | Built-in |
| Goose | [github.com/block/goose](https://github.com/block/goose) | Built-in (>= 1.8.0) |
| Kiro | [kiro.dev](https://kiro.dev) | Built-in (>= 1.25.0) |
| Mistral Vibe | N/A | `uv tool install mistral-vibe` or `pip install mistral-vibe` |
| OpenCode | [opencode.ai](https://opencode.ai) | Built-in (>= 1.0.0) |

After installing, restart JupyterLab. The agent will appear as an @-mentionable persona automatically.

## Creating a Custom ACP Persona

Subclass `BaseAcpPersona` and provide an `executable`:

```python
from jupyter_ai_acp_client import BaseAcpPersona
from jupyter_ai_persona_manager import PersonaDefaults
import os

class MyAgentPersona(BaseAcpPersona):
    def __init__(self, *args, **kwargs):
        executable = ["my-agent-acp"]  # command to start the ACP server
        super().__init__(*args, executable=executable, **kwargs)

    @property
    def defaults(self) -> PersonaDefaults:
        return PersonaDefaults(
            name="MyAgent",
            description="My custom ACP agent.",
            avatar_path=os.path.join(os.path.dirname(__file__), "avatar.svg"),
            system_prompt="unused"  # ACP agents manage their own prompts
        )
```

Register via entry point in `pyproject.toml`:
```toml
[project.entry-points."jupyter_ai.personas"]
my-agent = "my_package:MyAgentPersona"
```

## Key Implementation Details

- `BaseAcpPersona` creates subprocesses lazily — shared across all instances of the same persona class
- The ACP client handles streaming, tool calls, and permission requests
- File read/write and terminal use go through the ACP client's capability system
- All operations are subject to the permission system (user must approve writes/executes)
