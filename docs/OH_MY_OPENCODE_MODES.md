# Oh My OpenCode Agent Modes

This documentation explains the special operating modes provided by the “Oh My OpenCode” (OmO) plugin. This plugin replaces the standard OpenCode agent with a more advanced orchestrator.

## 1. Sisyphus (The Orchestrator)
**Default Mode / Primary Agent**

Sisyphus is the main agent in “Oh My OpenCode”. Its name is taken from Greek mythology, symbolizing relentless hard work—but in this context, it works smart by delegating workload.

### Characteristics:
* **Orchestrator:** Doesn't do everything itself. Sisyphus is designed to break down big problems and delegate tasks to *sub-agents* (such as `oracle`, `librarian`, or `coder`).
* **Todo-Driven:** Relies heavily on `TodoWrite` and task list management to track progress on complex jobs.
* **Background Worker:** Able to run tasks in the background while you do other things.
* **Model:** Typically uses the smartest model (such as Claude 3.5 Opus/Sonnet) with an *extended thinking budget* for high-level planning.

### When to Use Sisyphus?
* **Daily:** This is your default mode. Use it for almost all general coding interactions.
* **Complex Projects:** When tasks require multiple steps (edit file A, then update test B, then refactor C).
* **Delegation:** When you want to say “Please fix all these linter errors” and let it call sub-agents to work on them in parallel. 

---

## 2. Planner-Sisyphus (The Architect)
**Planning Mode**

Planner-Sisyphus is a variant of Sisyphus that runs in OpenCode's “Plan” mode, but with OmO orchestration capabilities.

### Characteristics:
* **Read-Only (Usually):** Focuses on analysis, reading files, and strategizing without directly modifying code (depending on configuration, usually the `write` tool is disabled or restricted).
* **Strategic:** Used to see the big picture of the architecture before Sisyphus (Worker) starts getting its hands dirty with code.
* **Output:** Generates a plan document (Markdown) that can then be executed by the `superpowers:writing-plans` or `superpowers:executing-plans` skill.

### When to Use Planner-Sisyphus?
* **Early Feature Phase:** Before writing a single line of code. Use it to analyze the repository and create an *Implementation Plan*.
* **Difficult Bug Analysis:** When you're stuck and need a “thinking partner” to trace the logic without the risk of breaking the code.
* **Architecture Review:** Seeking opinions on project structure or *best practices*.

---

## Workflow Summary

The best combination using Superpowers + Oh My OpenCode:

1.  **Analysis:** Use **Planner-Sisyphus** + the `Brainstorming` skill to understand the problem.
2.  **Plan:** Use **Planner-Sisyphus** + `Writing Plans` skill to create the `docs/plans/....md` file.
3.  **Execute:** Switch to **Sisyphus** + `Subagent Driven Development` skill to execute the plan task-by-task with the help of sub-agents.