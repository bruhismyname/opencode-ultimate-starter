# MCP (Model Context Protocol) Setup Guide

MCP allows your AI Agent to use external tools like Browsing, Database, or UI Libraries. This Starter Kit includes configuration for powerful Fullstack tools.

## Included Tools

### 1. Built-in Tools (Default)
These usually come pre-installed with `oh-my-opencode` or OpenCode core. You don't need extra config for these, but verify they are "Enabled" in your status bar.

* **`websearch_exa`**: Allows the AI to browse the real-time internet.
    * *Usage:* "Search for the latest Next.js 15 breaking changes."
* **`grep_app`**: Search code snippets across GitHub without cloning.
    * *Usage:* "Search how to implement Auth.js in a SvelteKit app using grep."
* **`context7`**: Intelligent context manager for documentation.

### 2. Custom Tools (Included in this Kit)
We have added configurations for **Frontend (Shadcn)** and **Backend (Supabase)**.

* **`shadcn` (Local)**:
    * *Function:* Add UI components directly to your project.
    * *Usage:* "Add a Button and Card component from shadcn."
* **`supabase` (Remote)**:
    * *Function:* Connect to your database to view tables, run queries, or create migrations.
    * *Usage:* "Check the `users` table schema and create a migration to add a `phone` column."

---

## Configuration (opencode.json)

To enable the Custom Tools, update your `opencode.json` with the `mcp` block below.

**! IMPORTANT:**
1.  Set `"enabled": true`.
2.  For Supabase, you must generate your own **Personal Access Token**.

```json
{
  "plugin": [
    "oh-my-opencode"
  ],
  "mcp": {
    "shadcn": {
      "type": "local",
      "command": ["npx", "-y", "shadcn", "mcp"],
      "enabled": true
    },
    "supabase": {
      "type": "remote",
      "url": "https://mcp.supabase.com/mcp",
      "enabled": true,
      "headers": {
        "Authorization": "Bearer YOUR_SUPABASE_ACCESS_TOKEN_HERE"
      }
    }
  }
}

### How to Get Supabase Token
Since automatic browser login often fails in terminal environments, we use a Personal Access Token (PAT).

1. **Login** to [Supabase Dashboard](https://supabase.com/dashboard).
2. Go to **Account Settings** -> **Access Tokens**.
3. Click **Generate new token**.
4. **Copy the token** (starts with `sbp_...`).
5. Paste it into `opencode.json` replacing `YOUR_SUPABASE_ACCESS_TOKEN_HERE`.

> **Note:** Keep the word `Bearer` before the token.