# Context Engineering, Claude Code And The PRP Framework Workshop

A hands-on, production-focused workshop teaching software teams to ship faster and with higher quality using **Context Engineering** principles, the **PRP Framework**, and **Claude Code**.

**Instructor:** [Ernesto Buttó](https://www.ernestobutto.com/)
**Primary Tool:** [Claude Code](https://www.claude.com/product/claude-code)
**PRP Framework:** [PRPs-agentic-eng](https://github.com/Wirasm/PRPs-agentic-eng) by [Rasmus Widing](https://www.rasmuswiding.com/)
**Format:** Virtual, 4 sessions


---

## 👥 Who This Is For

This workshop is designed for anyone involved in software delivery:
- Software Engineers & Engineering Managers
- Product Managers
- QA Engineers
- DevOps Engineers

**Prerequisites:**
- Basic understanding of software development workflows and git/GitHub
- Active project or codebase you're currently working on
- Ability to experiment with AI tools in your development workflow

---

## 🏗️ Workshop Approach

This is a **hands-on, production-focused workshop**. You'll learn by doing.

**Between sessions, you will:**
- Apply learned techniques to your current work
- Use Claude Code for actual tasks and features you're building
- Experiment with the PRP Framework in your team's codebase
- Track your progress and bring questions/insights to each session

---

# Session 1: Foundations

## Context Engineering & PRP Framework Workshop

**Instructor:** [Ernesto Buttó](https://www.ernestobutto.com/)**Primary Tool:** [Claude Code](https://www.claude.com/product/claude-code)**PRP Framework:** [PRPs-agentic-eng](https://github.com/Wirasm/PRPs-agentic-eng) by [Rasmus Widing](https://www.rasmuswiding.com/)

## What You'll Experience Today

1. **Understand** why context is so important
2. **See** a complete feature built in using good context engineering with Claude Code and the PRP framework.
3. **Learn** about the basic PRP workflow: `prp-base-create -> prp-base-execute` and it's related principles

### Main Topics

- Define the challanges
- Context Engineering: Beyond the tools
- Introduction to Claude Code + PRP Framework
- Demo video with Claude Code and the basic PRP workflow
- Q&A

## Why do A.I. Agents fail (in general)?

Quick Poll

- "Who's used AI coding tools?"
- "Who's been frustrated when AI doesn't get it?"

It’s usually because the LLM call inside the agent took the wrong action / didn’t do what we expected. LLMs fail for a few reasons:

1. The underlying LLM is not capable enough
2. The “right” context was not passed to the LLM
3. Agents System prompt might get in the way

More often than not - it’s actually the second reason that causes agents to not be reliable.

- https://docs.langchain.com/oss/python/langchain/context-engineering

## Why do A.I. Coding Agent fail?

- Vague requirements lead to incomplete implementations
- Missing context squeezes out useful tokens
- No tool access or access to wrong tools or knowledge on how to use them prevent agent to work autonomously
- No validation gates allow defects to accumulate
- Brittle code that breaks in production

## The PRP Solution based on Context Engineering

- Explicit implementation strategies
- Built-in validation and quality gates
- Everything fine tuned for a project
- Structured prompts with complete context
- Production-ready code on the first pass
- Ship robust, production-ready systems

### The Analogy

Think about onboarding a new engineer:

- You don't just say "fix the bug" and disappear
- You give them:
    - Codebase access
    - Documentation
    - Tools
    - Team conventions
    - Context about past decisions
    - Someone to ask questions

**AI agents need the same thing.**

But because they are not human, we need to organize the project for them in a different way. (Paradigm shift)

## Agentic Coding Tools vs Copilots vs Models

- Copilot story: It’s not the same to use *Claude Sonnet* with **Cursor** than with **Claude Code.** Why?
    - Celonis Developer Story of Cursor vs Claude Code both using Sonnet for the same feature.
        - Same prompt worked for Claude Code, not Cursor. Why?
- It's not the same using the tools as copilots than as agents. Why?

## What is Context Engineering

After a few years of prompt engineering being the focus of attention in applied AI, a new term has come to prominence: **context engineering**. Building with language models is becoming less about finding the right words and phrases for your prompts, and more about answering the broader question of *“what configuration of context is most likely to generate our model’s desired behavior?"*

**Context** refers to the set of tokens included when sampling from a large-language model (LLM).

The **engineering** problem at hand is optimizing the utility of those tokens — in other words: considering the holistic state available to the LLM at any given time and what potential behaviors that state might yield.

- https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents

<img src="resources/images/callibrating-prompt.png" alt="callibrating-prompt" width="500"/>

## The PRP Framework

Help us integrate all of these concepts conviniently, fast and properly, allowing us to custumize it and acquire an instict.

- Research → Plan → Review → Execute cycle
- `prp-base-create -> prp-base-execute`

## The Demo: Delete a Blueprint

Basic Workflow 1.

**Demo Video:** https://youtu.be/CpmhipO4yR0

Conversations and Q&A

## Post Demo: Step by Step Dive

- Review the [prp-base-create](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/.claude/commands/prp-commands/prp-base-create.md) command step by step
- Review the [prp-base-execute](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/.claude/commands/prp-commands/prp-base-execute.md) command step by step

---

**Break**

---

## Why learn Context Engineering Skills

- It’s a skill that as you become better, it gets you closer to building production ready code in the first try
- As you understand the principles through practice using the PRP framework, you can
    - Use other Coding Agents besides Claude Code
    - User other Frameworks besides the PRP framework
- You can ship quality + speed, which has been usually a tradeoff. Example of TDD for me, sometimes is the only way it works.
- Levels up our knowledge faster, forcing us to review and understand the plans
- It’s fun

## Install Claude Code

- https://code.claude.com/docs/en/quickstart
- Ask if everyone has Claude Code installed and help.

## The 4 Context Strategies

### 1. Writing Context

Storing important information outside the immediate context window, such as plans, notes (scratchpads), or memories that persist across sessions. This helps agents retain critical knowledge without overcrowding their working memory.

- [CLAUDE.md](http://claude.md/) files, plans, notes
- Persistent memory across sessions
- Stores team conventions automatically

### 2. Selecting Context

Dynamically choosing the most relevant pieces from saved context or memory to bring into the working context window as needed.

- Dynamically choose what to load
- Search for relevant files only
- Don't dump entire codebase

### 3. Compressing Context

Summarizing or pruning context content to fit within the token limits while preserving essential information. This reduces noise, cost, and latency. Techniques include recursive summarization, hierarchical summarization, or using specialized summarization models.

- Summarize large documents
- Distill to essentials
- Fit more meaningful info in limited space

### 4. Isolating Context

Splitting up context into isolated environments or sub-agents to handle different subtasks, thus maintaining focused context windows for each agent. For example, multi-agent systems or sandboxed environments to separate heavy data like images or audio.

- Separate agents for separate tasks
- Research → Plan → Execute
- Focused agents = better results

---

## The Difference

```
❌ Bad Context:
- Vague prompts
- No project documentation
- Full codebase dump
- No conventions

= Confused AI = Bad code = Hours of iteration

✅ Good Context:
- Clear project docs (CLAUDE.md)
- Relevant files only
- Compressed summaries
- Focused sub-agents

= Smart AI = Production code = Minutes to success

```

---

## Activities

- Create your first CLAUDE.md
- Experiment with plan mode on real tasks
- Experiment with pure PRP no plan mode for a real issue.
- Read [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)

---

## What's Coming Next

### PRP

- [Common Mistakes](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#common-mistakes-dont-do-these-)
- The Task workflow
- [Longer Workflows](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#the-magic-how-they-work-together-): The Master planning → Technical specs → Implementation manual → Build new feature
- Personalizing templates
    - Base templates
    - Execute templates
- Good Vs Bad Practices
- More about [Chaining Workflows](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#-command-chaining)
- [Command list by Categories](https://github.com/Wirasm/PRPs-agentic-eng/blob/development/README-for-DUMMIES.md#command-categories-quick-reference-)

### Agentic A.I.

- gemini code review
- Working on 2 branches at once
- ultrathink and other keywords
- Detailed PRs
- Detailed commits
- Thoughts on a review using 'gh cli'
- VCS / Git operations (merge, rebase, branching
- MCPs: Jira, Context7, MPC Browser and Playwrite, Figma
- Generate changelog and documentation (show my documentation command)
- Claude Code Planning mode resembles the PRP experience, but I find it much less reliable

---

## Resources

### Essential Links

- [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices)
- [PRP Framework Repository](https://github.com/Wirasm/PRPs-agentic-eng)
- [Effective Context Engineering](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

### Demo Video

- [Delete a Blueprint Demo](https://youtu.be/CpmhipO4yR0)

### Support

- TBD

---

*This workshop is brought to you by [Ernesto Buttó](https://www.ernestobutto.com/), using the [PRP Framework](https://github.com/Wirasm/PRPs-agentic-eng) by [Rasmus Widing](https://www.rasmuswiding.com/)*