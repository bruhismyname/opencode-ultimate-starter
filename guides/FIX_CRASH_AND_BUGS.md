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

## 2. Fix: Superpowers Installation Failed (Symlink Error)
**Symptom:** OpenCode crashes or shows "Module not found" when trying to load Superpowers.
**Cause:** The official installation guide uses `ln -sf` (Linux command). On Windows, this fails to create a proper link to the plugin file, or creates a broken file.

**Solution (The "PowerShell" Way):**
Instead of using the Linux command, follow these steps to install Superpowers correctly on Windows:

1.  **Remove Old/Broken Files:**
    Go to `%USERPROFILE%\.config\opencode\plugin\` and delete `superpowers.js` if it exists (it's likely 0kb or broken).

2.  **Open PowerShell as Administrator** (Recommended).

3.  **Run these commands sequentially:**

    ```powershell
    # 1. Create directory and clone the repo (if not already done)
    mkdir -p $HOME\.config\opencode\superpowers
    git clone [https://github.com/obra/superpowers.git](https://github.com/obra/superpowers.git) $HOME\.config\opencode\superpowers

    # 2. Create the Plugin folder
    mkdir -p $HOME\.config\opencode\plugin

    # 3. Create the Symlink correctly (The Magic Step)
    New-Item -ItemType SymbolicLink -Path "$HOME\.config\opencode\plugin\superpowers.js" -Target "$HOME\.config\opencode\superpowers\.opencode\plugin\superpowers.js"
    ```

4.  **Verify:**
    Check if `superpowers.js` appears in your `.config\opencode\plugin` folder with a shortcut arrow icon.

5.  **Alternative (Manual Copy):**
    If the symlink method still fails due to permissions, you can copy the file manually (Note: You won't get auto-updates):
    ```powershell
    Copy-Item $HOME\.config\opencode\superpowers\.opencode\plugin\superpowers.js $HOME\.config\opencode\plugin\superpowers.js
    ```