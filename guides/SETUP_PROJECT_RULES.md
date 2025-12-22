# Automate AI Discipline with `AGENTS.md`

One of the hidden but very powerful features of `oh-my-opencode` is the **Directory Agents Injector**.

This feature allows you to automatically “embed” work rules (SOP) into each project. The AI will read this file before starting work, so it will always comply with the workflow you specify.

## How to Use It

### Step 1: Create a File in Your Project
In the root folder of the **application project** you are working on (not the OpenCode config folder), create a new file named:

`AGENTS.md`

### Step 2: Fill in the “Rules of Engagement”
Copy the rule template below. These rules are designed so that the AI (Planner-Sisyphus) automatically creates a work plan (`todos.md`), records changes (`CHANGELOG.md`), and commits git neatly.

```markdown
# Project Workflow Rules

You are strictly required to follow these workflow rules for every task.

## 1. Master Plan (todos.md)
- **Initiation**: If `todos.md` does not exist, CREATE IT immediately using `Planner-Sisyphus`.
- **Structure**: The file must contain a comprehensive list of tasks from development start to finish.
- **Status**: Use `[ ]` for pending and `[x]` for completed tasks.
- **Update**: You MUST mark tasks as `[x]` immediately after completion.

## 2. Change Tracking (CHANGELOG.md)
- **Initiation**: If `CHANGELOG.md` does not exist, create it.
- **Format**: Use Keep A Changelog format (Unreleased, Added, Changed, Fixed).
- **Update**: Every time you complete a meaningful task or modify code behavior, append a bullet point to the `Unreleased` section.

## 3. Version Control (Git)
- **Commit**: You must commit changes after every logical unit of work (e.g., after completing a single item in `todos.md`).
- **Message**: Commit messages must be descriptive (e.g., `feat: implement login page UI`, `fix: resolve jwt token error`).
- **History**: Ensure the git history tells a clear story of the development process.

## 4. Execution Protocol
- BEFORE starting coding: Check `todos.md`.
- AFTER coding:
  1. Run tests/verification.
  2. Update `CHANGELOG.md`.
  3. Mark item in `todos.md` as `[x]`.
  4. Git add & commit.
```

### Step 3: Restart Session
Close your current OpenCode session, then reopen it. `oh-my-opencode` will detect the `AGENTS.md` file and inject the above instructions into the AI system prompt.

Now, every time you ask the AI to work, it will automatically check `todos.md` and `CHANGELOG.md` without needing to be reminded!

---