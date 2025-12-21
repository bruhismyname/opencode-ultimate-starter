# OpenCode Prompt Cheat Sheet: Planner Mode (Token Saver) 🇺🇸

This mode treats the AI as the **Architect** and you as the **Builder**. The AI does **not** edit files directly (saving tokens), but provides final code for you to copy-paste.

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