---
layout: section
_meta:
  duration: 15min
  outline:
    - Jupyter development is challenging — barrier to contribution
    - Jupyter AI is a complex extension, compounding the problem
    - This barrier can be lowered — we have the technology
    - Invest in the developer experience to drive exponential growth
    - Build the features that really count, work backwards from users
    - Be picky with what we develop — dedicate time to opening the gates
---

# Thinking ahead: AI and Jupyter

--- 

# Jupyter is important

Project Jupyter is bigger than many people realize!

<v-clicks>

- Jupyter Notebooks were used to analyze data from the LIGO interferometer to detect **gravitational waves**, the confirmation of which was awarded the 2017 Nobel Prize in Physics.
- NASA uses Jupyter to analyze data from various telescopes and satellites, including from the JWST!
- Jupyter is used at banks, hedge funds, and other financial institutions for quantitative analysis.
    - D.E. Shaw, UBS, Stripe, Bloomberg 
- Computational notebooks are used by teams of machine learning scientists and engineers across the world.
    - Apple, Databricks, Snowflake, and lots of AWS customers
- Project Jupyter won the 2017 ACM Software Systems award
- Repos containing Jupyter notebooks grew by **1 million** in 2025 (**+75% YoY**)

</v-clicks>

---

# Questions raised by the emergence of AI

(even if you are an AI skeptic, like I once was)

<v-clicks>

- Agents are getting better (genuinely surprising!)
- The way that software engineers work has been transformed by AI in ~1 year
    - Claude Code was released March 2025
- Then, naturally, 2 questions follow:

</v-clicks>
<v-clicks depth=99>

1. **AI *in* Jupyter**: How will Jupyter's audience of researchers, scientists, and engineers be using AI in 1 year?
    - What about 2? 3? 5?
    - Think about how AI interaction has changed in the last year.
    - From a broader view: the 'AI chat experience' is really just the first step.
2. **AI *for* Jupyter**: How will Project Jupyter evolve as AI continues to grow?
    - Can AI unlock ambitious, cross-cutting contributions which we did not think were possible before?
    - Can AI generate truly good code? Can we reduce the burden AI places on maintainers? 

</v-clicks>

---

# Human-AI interfaces will evolve as AI evolves

Ideas about AI *in* Jupyter (1)

<v-clicks>

- Human-computer interfaces (HCIs) evolved dramatically in the last 50 years. The keyboard and mouse were not born alongside the computer.
    - Not even the monitor. (TTY := teletypewriter)
- Now these new HCIs are ubiquitous. Why? **Computers and computer hardware got better.**
- **So what happens when AI and AI environments get better?**
- Agents are now more steerable and reliable. The skills + MCP ecosystem have grown remarkably. What is this changing?
    - People are building **agent control planes (semi-autonomous)** that provide an interface for you to *teach* multiple agents what to do instead of *telling* one agent what to do. (see Antigravity, Cursor, etc.)
- What lies ahead?
    - Agent orchestrator (fully-autonomous): an environment that allows agents to work autonomously, learn automatically, and ship safely (OpenAI Symphony)
- The key idea: *as agents capabilities improve and AI environments mature, the human-AI interface will change*.

</v-clicks>
---

# AI challenges perceived limits on project growth

Ideas about AI *for* Jupyter (2)

<v-clicks>

- `cmux`: a multiplexer for managing multiple workspaces with dedicated terminals, agent sessions, browsers.
- Offers a CLI and skill suite allowing agents to use `cmux`
    - Agents can spawn new workspaces and work on separate tasks in parallel
    - Allows agents to open browsers and interact with the DOM and JS engine
- 2 engineers are opening 1 PR *per hour*. EACH.
- One release in 5 days: 55,000 lines of code changed
- And somehow... it still works! Really well, I should add.
    - What does this mean?
- In this new era: **don't let existing notions of feasibility limit your imagination.**

</v-clicks>

---

# Realize the potential of the present

Concluding thoughts before we jump into launching the discussion and collaboration.

<v-clicks>

- The few dozen people we have in this room are thinking about the intersection of two incredibly valuable technologies that have enormous potential to benefit the greater good.
- Don't be afraid to voice big ideas you have no idea are feasible.
- Feel free to call out and challenge existing features, concepts, or limitations.
- Don't feel pressured to write code if you aren't familiar with the codebase. You can learn it later and use this time to collaborate. We will happily guide each of you along the way.
- There is enormous value in design, prototyping, experimentation, and documentation.

</v-clicks>
