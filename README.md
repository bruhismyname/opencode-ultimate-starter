# OpenCode Ultimate Starter Kit & Fixes
**(Unofficial Guide: Stability Fixes + Planner Mode Strategy)**

This repository provides configuration templates, critical crash fixes for Windows users, and prompt strategies for getting the most out of **OpenCode**, **Oh My OpenCode**, and **Superpowers**.

## The Problems We Solved
1. **Windows Native Crash**: Fixing the `exit_code: -1073740791` caused by corrupted config parsers.
2. **Missing Superpowers Lib**: Fixing the `plugin/superpowers.js` error due to missing `lib/skills-core.js`.
3. **Token Consumption**: A strategy to reduce token usage by 70% using "Planner-Sisyphus Mode".

## Repository Contents

- **[configs/](configs/)**: Clean JSON templates that won't break your OpenCode installation. *(Disclaimer: These configurations use GitHub Copilot as the model)*.
- **[guides/FIX_CRASH_AND_BUGS.md](guides/FIX_CRASH_AND_BUGS.md)**: Step-by-step technical solutions for installation errors.
- **[prompts/CHEATSHEET_ID.md](prompts/CHEATSHEET_ID.md)**: (Bahasa Indonesia) Strategi hemat token dengan mode Planner.
- **[prompts/CHEATSHEET_EN.md](prompts/CHEATSHEET_EN.md)**: (English) Token-saving prompt strategies.
- **[guides/SETUP_PROJECT_RULES.md](guides/SETUP_PROJECT_RULES.md)**: Cara memaksa AI bekerja disiplin (Auto-create TODOs & Changelog) menggunakan `AGENTS.md`.

## Quick Setup
1. **Install Prerequisites**: Follow the steps in **[INSTALL_GUIDE.md](INSTALL_GUIDE.md)** to install OpenCode, Oh My OpenCode, and Superpowers.
2. **Apply Fixes**: Copy the contents of `configs/` to your local `.config/opencode/` directory.
3. **Start Coding**: Run `opencode` and enjoy!

## Contributing
If you have found better configurations or new prompt tricks, feel free to open a Pull Request!

---
*Disclaimer: This is a community-contributed guide and is not affiliated with the official OpenCode team.*