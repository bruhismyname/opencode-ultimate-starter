# Troubleshooting Guide: Crashes & Superpowers Errors

## 1. Fix: Native Crash on Windows (`exit_code: -1073740791`)
**Symptom:** OpenCode closes immediately upon opening.
**Cause:** The `opencode.json` file contains a `$schema` line or formatting that crashes the native Windows binary parser.

**Solution:**
1. Navigate to `%USERPROFILE%\.config\opencode\`.
2. Delete or rename the existing `opencode.json`.
3. Create a new `opencode.json` with **minimal content**:
   ```json
   { "plugin": ["oh-my-opencode"] }
   ```
> ⚠️ **Important:** Right-click the file > Properties > Check "Read-only". This prevents OpenCode from auto-injecting the crashing `$schema` line again.

## 2. Fix: Superpowers "Module Not Found"
**Symptom:** Error loading `plugin/superpowers.js` stating it cannot find `../../lib/skills-core.js`.
**Cause:** Manual installation often misses the `lib` folder.

**Solution:**
Ensure your folder structure looks exactly like this:

```text
.config/opencode/
├── opencode.json
├── plugin/
│   └── superpowers.js
├── lib/                 <-- MUST EXIST
│   └── skills-core.js   <-- Download from Superpowers Repo
└── skills/              <-- MUST EXIST
```

If missing, download `skills-core.js` manually from the official Superpowers repository and place it in a `lib` folder.