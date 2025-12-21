# OpenCode Prompt Cheat Sheet: Planner Mode (Token Saver) 🇺🇸

This mode treats the AI as the **Architect** and you as the **Builder**. The AI does **not** edit files directly (saving tokens), but provides final code for you to copy-paste.

## Key Principles
1. **Architect Mode:** Let the AI think first, don't start coding right away.
2. **Use Tools:** Force the AI to use MCP (Database/Terminal) instead of guessing.
3. **No Edit:** Request the final output in the chat for copy-pasting (except for small tasks).

### The Golden Rule
Append this to your prompts:
> **"Do not execute any commands or edit files. Just provide the detailed plan/code in the chat response for me to copy-paste."**

### Scenario Table

| Goal | Prompt Template |
| :--- | :--- |
| **New Feature / Idea** | "Act as **Sisyphus**. I have an idea for [Feature]. Use the **`brainstorming`** skill to clarify requirements. Then, create a detailed implementation plan." |
| **Backend Logic** | "Act as **@oracle**. I need a function to handle [Logic]. Write the **complete code** with error handling. Do not use placeholders." |
| **UI/UX Design** | "Act as **@frontend-ui-ux-engineer**. Create a [Component Name] using [Tailwind/CSS]. Focus on accessibility. Provide full code ready to copy-paste." |
| **Debugging** | "I have this error: `[Paste Error]`. Use **`systematic-debugging`** logic. Don't run tests yourself. Analyze the root cause and tell me what to fix." |

---

## Section 1: Automated Workflow (Required `AGENTS.md`)
*Use this if you have already installed `AGENTS.md` in your project.*

| Purpose | Magic Prompt |
| :--- | :--- |
| **Start New Feature** | “I want to create a feature called [Feature Name]. According to the rules in `AGENTS.md`, please: <br>1. Analyze the requirements.<br>2. Update `todos.md` with a detailed list of tasks.<br>3. Don't code yet, confirm the plan with me first.” |
| **Update Progress** | “I have completed [Task Name]. Please update `todos.md` (mark as complete) and add an entry to the Unreleased section of `CHANGELOG.md`.” |

---

## Part 2: Using MCP (Superpowers)
*Use this to leverage the Shadcn, Supabase, and Web Search tools.*

| Tool | Scenario | Powerful Prompt |
| :--- | :--- | :--- |
| **Supabase** | **Check Database** | “Use **Supabase MCP** to view the table structure of `[table_name]`. Based on that schema, create an SQL query/TypeScript function to retrieve data X.” |
| **Supabase** | **Debug Data** | "There is an error when inserting data. Check the last 5 rows of the `[table_name]` table via Supabase MCP to see the correct data format." |
| **Shadcn** | **Install UI** | “Use **Shadcn MCP** to add the `[component_name]` component (e.g., button, card). Do not edit manually, use the tool.” |
| **Web Search** | **Find Latest Info** | “Use **Web Search** to find the latest solutions for the error `[Paste Error]`. Don't use old knowledge, look for solutions from 2024/2025.” |
| **Grep** | **Search for References** | “I need an example of [Library Name] implementation. Use the **Grep Tool** to find real coding examples on GitHub.” |

---

## Part 3: Coding & Planner (Token Savings)

| Purpose | Powerful Prompt |
| :--- | :--- |
| **Backend Logic** | “Act as **@oracle**. I need an API function for [Explain Logic]. Write **complete code** with error handling. Do not use placeholders.” |
| **Frontend UI** | “Act as **@frontend-ui-ux-engineer**. Create the [UI Name] component using the installed Shadcn component. Focus on the visual hierarchy.” |
| **Refactoring** | "The code in the [File Name] file is too messy. Refactor it to make it cleaner (Clean Code) without changing its main function. Explain what you changed." |

### Pro Tips
* **If Supabase Error:** Make sure the token in `opencode.json` is still valid.
* **If Shadcn Error:** Make sure your project has been initialized with `npx shadcn@latest init` beforehand.