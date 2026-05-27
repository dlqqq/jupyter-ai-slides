---
layout: section
_meta:
  duration: 15min
  outline:
    - TBD
---

# Development Tracks

---

# How we will collaborate

- Here, we'll propose a list of "development tracks" which each describe big ideas that could shape the future of Jupyter AI.

- For those who want to contribute directly: `jupyter-ai-contrib/jupyter-ai-devrepo`

- Also see the Contributing Guide in the documentation

---

# Design/coding track: dynamic AI personas

<v-clicks>

- Issue: It's too hard to make custom agents (AI personas) in Jupyter AI

- Idea part 1: Design the API/skills/tools that would allow for agents to create custom, domain-specific AI personas at runtime

- Idea part 2: Decouple the implementation (agent harness) from the definition (AI persona)

- Vision: `@Claude Create me an AI persona that can analyze satellite images. Use the notebooks in ./analysis to learn the patterns our research staff use and what are the key findings we wish to assess in each dataset. You can use Claude as the base agent harness.`

- Places to look: `jupyter-ai-contrib/jupyter-ai-persona-manager`

</v-clicks>

---

# Experimentation track: Jupyter AI on JupyterHub

<v-clicks>

- Issue: We have absolutely no experience using JupyterHub.

- Idea: Try deploying Jupyter AI on JupyterHub and see how far you get, document the steps a user would need to take, and call out any roadblocks you find along the way.

- Places to look: `jupyterlab/jupyter-ai` (this is where the documentation source lives)

</v-clicks>

---

# Experimentation track: Jupyter AI for YOU

<v-clicks>

- Issue: We could use more help in verifying Jupyter AI is helpful to Jupyter's audience.

- Idea: Try customizing the AI personas using MCP servers and skills, then see how useful it can be for a specific use-case you have. Document any gaps you find along the way.

- Places to look: Jupyter AI user guide (includes more info on configuring MCP servers)

</v-clicks>

---

# Design track: New Human-AI interfaces

<v-clicks>

- Issue: Right now, Jupyter AI is mainly just a chat-oriented experience.

- Idea 1: Maybe an AI experience inside the notebook UI itself?

- Idea 2: Agent control plane UI? Configure MCP servers, skills, and more?

- Idea 3: Some sort of task manager that dispatches agents autonomously?

- Places to look: Piyush's HTML prototypes (will share link)

</v-clicks>

--- 

# Coding track: `nb-cli` + `jupyter-ai-tools`

<v-clicks>

- Issue: Jupyter AI's toolkit of notebook-native tools doesn't use `nb-cli` yet. 

- Idea: Edit `jupyter-ai-tools` to automatically detect when `nb-cli` is installed. Then use that to implement the notebook tools if installed.

- Or maybe we just disable the `jupyter-ai-tools` we provide when `nb-cli` is installed, since the agent can just run `nb-cli` on the terminal to do things.

- Places to look: `jupyter-ai-contib/{nb-cli,jupyter-ai-tools}`

</v-clicks>

---

# Design track: Generalizing `nb-cli`?

<v-clicks>

This is not really an issue, but more of a bigger idea I wanted to throw out there.

Agents are great at using CLIs. Do we ultimately want something like `jl-cli` to provide AI agents with a unified interface to fully control the JupyterLab workspace?

What possibilities could this unlock? What would we want it to do for it to be useful?

Places to look: `cmux` documentation, `nb-cli`

</v-clicks>

---

# Documentation track

<v-clicks>

- Issue: Lots of our repos lack more detailed documentation on architecture. This limits how useful agents can be out-of-the-box when building Jupyter AI, and raises the barrier to contribution.

- Idea: Contribute documentation along the way as you learn how to work with Jupyter AI! `AGENTS.md` files, Jupyter AI docs, etc. All contributions welcome.

</v-clicks>
