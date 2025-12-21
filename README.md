# OpenCode Ultimate Starter Kit (Fullstack Edition)
**(Unofficial Guide: Crash Fixes + MCP Tools + Planner Strategy)**

This repository is the "missing manual" and "starter pack" for **OpenCode** users, especially on Windows. It combines stability fixes with advanced configurations for a modern Fullstack development workflow.

> **Status:** Updated for OpenCode v1.0+ | Supports Oh My OpenCode & Superpowers

## Why Use This Kit?

### 1. Stability Fixes (Anti-Crash)
Solves the infamous `exit_code: -1073740791` on Windows and the "Superpowers module not found" error.

### 2. God-Mode Tools (MCP Support)
Pre-configured setups for **Model Context Protocol (MCP)**.
- **Frontend:** Install **Shadcn** components via chat.
- **Backend:** Connect to **Supabase** (Postgres) to query data & verify migrations.
- **Web:** Browse the internet for real-time docs (via Exa).

### 3. Auto-Discipline Agent
Includes a "Project Rules" injector (`AGENTS.md`) that forces the AI to:
- Auto-maintain `todos.md` (Master Plan).
- Auto-update `CHANGELOG.md`.
- Follow strict Git commit standards.

### 4. Token-Saving Strategy
A specialized Cheat Sheet to use the "Planner-Sisyphus" mode effectively, saving you 70% of tokens while maintaining high-quality code.

---

## Documentation Map (Peta Panduan)

| File / Guide | Description |
| :--- | :--- |
| **[`INSTALL_GUIDE.md`](INSTALL_GUIDE.md)** | **Start Here!** How to install OpenCode, Oh My OpenCode, & Superpowers correctly. |
| **[`guides/FIX_CRASH_AND_BUGS.md`](guides/FIX_CRASH_AND_BUGS.md)** | Solution for Windows native crashes & Symlink errors. |
| **[`guides/MCP_SETUP.md`](guides/MCP_SETUP.md)** | **New!** How to enable Supabase, Shadcn, & Web Search tools. |
| **[`guides/SETUP_PROJECT_RULES.md`](guides/SETUP_PROJECT_RULES.md)** | **New!** How to automate AI workflow with `AGENTS.md`. |
| **[`prompts/CHEATSHEET_ID.md`](prompts/CHEATSHEET_ID.md)** | (Bahasa Indonesia) Strategi Prompt Planner & penggunaan Tool MCP. |
| **[`configs/`](configs/)** | Safe JSON configuration templates (Clean & Valid). |

---

## Quick Start (3 Steps)

### 1. Install Core Components
Follow the instructions in **[`INSTALL_GUIDE.md`](INSTALL_GUIDE.md)** to get the base applications running.

### 2. Apply The Configs
Backup your existing `.config/opencode` folder, then copy the contents of the `configs/` folder from this repo to your local machine:
- `configs/opencode.json` -> Fixes crashes & sets up MCP.
- `configs/oh-my-opencode.json` -> Sets up Agent Personas (Oracle, Sisyphus, etc).

### 3. Activate "God Mode"
- Read **[`guides/MCP_SETUP.md`](guides/MCP_SETUP.md)** to add your Supabase Token.
- Read **[`guides/SETUP_PROJECT_RULES.md`](guides/SETUP_PROJECT_RULES.md)** to initialize your first project.

---

## Troubleshooting & Community
- **Issue:** "OpenCode closes immediately." -> See [Fix Guide](guides/FIX_CRASH_AND_BUGS.md).
- **Issue:** "Supabase MCP Failed." -> You likely need a Personal Access Token. See [MCP Guide](guides/MCP_SETUP.md).

*Disclaimer: This is a community-contributed repository and is not affiliated with the official OpenCode team.*