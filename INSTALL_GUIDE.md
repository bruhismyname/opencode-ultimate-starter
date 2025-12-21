# Installation Guide / Panduan Instalasi

This guide provides a quick summary of how to install the core components. For detailed documentation, please visit the official repositories linked below.

---

## 1. OpenCode (The Core Engine)
**Official Source:** [opencode.ai](https://opencode.ai) | [npm package](https://www.npmjs.com/package/opencode-ai)

### How to Install
Open your terminal (PowerShell/CMD/Bash) and run:
```bash
npm install -g opencode-ai
```

## 2. Oh My OpenCode (The Plugin Framework)
**Official Source:** [GitHub - code-yeongyu/oh-my-opencode](https://github.com/code-yeongyu/oh-my-opencode)

### How to Install
```bash
npm install -g oh-my-opencode
```
> ! **Important:** Do not edit `opencode.json` manually yet. Use the file provided in this Starter Kit (Step 4 below) to avoid crashes.

## 3. Superpowers (The Skills)
**Official Source:** [GitHub - obra/superpowers](https://github.com/obra/superpowers)

### How to Install
Once you can open OpenCode, run this command inside the OpenCode terminal:

```text
Fetch and follow instructions from [https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md](https://raw.githubusercontent.com/obra/superpowers/refs/heads/main/.opencode/INSTALL.md)
```

> **Troubleshooting:** If you see an error like `Module not found: lib/skills-core.js`, please refer to our fix guide: [guides/FIX_CRASH_AND_BUGS.md](guides/FIX_CRASH_AND_BUGS.md).

## 4. APPLY THE STARTER KIT (The Final Step)
This is where this repository shines. Instead of configuring everything manually and risking a crash, copy our safe configurations.

### Copy Instructions

1. **Locate your config folder:**
   - **Windows:** `C:\Users\YOUR_USERNAME\.config\opencode\`
   - **Mac/Linux:** `~/.config/opencode/`

2. **Back up your existing files** (if any).

3. **Copy files from this repository:**
   - Copy `configs/opencode.json` → Paste into config folder (Fixes startup crash).
   - Copy `configs/oh-my-opencode.json` → Paste into config folder (Sets up Agents).

4. **Restart OpenCode.**