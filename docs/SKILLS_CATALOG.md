# Superpowers Skills Catalog

A complete list of skills available in Superpowers and when to use them.

## Core Development Skills

### Brainstorming
**Skill Name:** `superpowers:brainstorming`
**Description:** Helps transform abstract ideas into designs and technical specifications through collaborative dialogue.
**When to use:**
* Before starting a new feature or complex component.
* When requirements are still unclear or need exploration.
* To generate design documents (`docs/plans/YYYY-MM-DD-topic.md`).

### Writing Plans
**Skill Name:** `superpowers:writing-plans`
**Description:** Write highly detailed implementation plans (task-by-task) based on specifications or brainstorming results.
**When to use:**
* After the design phase is complete.
* Before writing any code.
* To break large features into small steps (2-5 minutes per task) that are safe for AI to execute.

### Test Driven Development (TDD)
**Skill Name:** `superpowers:test-driven-development`
**Description:** Ensures that every piece of production code begins with a failing test (Red-Green-Refactor).
**When to use:**
* **ALWAYS** when writing new features or fixing bugs.
* To prevent regression and ensure code works as expected.
* *Iron Rule:* “No production code without a failing test first.”

## Execution & Workflow Skills

### Subagent Driven Development
**Skill Name:** `superpowers:subagent-driven-development`
**Description:** Execute implementation plans in the same session by sending specific sub-agents for each task.
**When to use:**
* When you already have a plan file (`docs/plans/...`).
* Tasks are independent and can be completed one at a time.
* Want fast iterations with an automatic *review loop* (Spec Review → Code Review) for each task.

### Executing Plans
**Skill Name:** `superpowers:executing-plans`
**Description:** Execute plans in separate sessions or *batch* mode with manual review checkpoints.
**When to use:**
* An alternative to *Subagent Driven Development* if you want tighter manual control.
* Run plans in a separate *git worktree*.

### Finishing a Development Branch
**Skill Name:** `superpowers:finishing-a-development-branch`
**Description:** A structured guide to completing work: verifying tests, then choosing a merge option (Local, PR, or Delete).
**When to use:**
* When feature implementation is complete.
* Before merging code into the main branch (`main`/`master`).
* To automatically clean up the *worktree*.

## Debugging & Review Skills

### Systematic Debugging
**Skill Name:** `superpowers:systematic-debugging`
**Description:** A mandatory investigation framework before fixing bugs. Prioritizes finding the root cause over guessing solutions.
**When to use:**
* Whenever there is a bug, test error, or strange behavior.
* **DO NOT** fix bugs without going through this investigation phase.

### Dispatching Parallel Agents
**Skill Name:** `superpowers:dispatching-parallel-agents`
**Description:** Dispatch multiple agents simultaneously to handle unrelated issues in parallel.
**When to use:**
* There are 3+ test files that fail with different causes.
* Issues in separate subsystems (no shared state).
* Want to speed up mass bug fixes.

### Requesting Code Review
**Skill Name:** `superpowers:requesting-code-review`
**Description:** Calls a special sub-agent (`code-reviewer`) to check the code before proceeding to the next stage.
**When to use:**
* After completing a major task.
* Before committing or merging.

### Receiving Code Review
**Skill Name:** `superpowers:receiving-code-review`
**Description:** Protocol for receiving review feedback. Teaches AI to verify feedback technically, not just agree (“performative agreement”).
**When to use:**
* When receiving feedback from human or AI reviewers.
* To ensure reviewer suggestions are valid and do not damage existing code.