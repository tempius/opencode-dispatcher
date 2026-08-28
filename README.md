# 🧠 opencode-dispatcher

A dynamic model routing engine for OpenCode Desktop that routes your prompts to the best free/Zen-tier model.

---

## 🛠️ Installation & Configuration Paths

To install the plugin globally, add the repository to your global `opencode.json` (or `opencode.jsonc`) configuration file's `plugin` array:

```json
{
  "plugin": [
    "dispatcher@git+https://github.com/tempius/opencode-dispatcher.git"
  ]
}
```

### 📍 Configuration & Asset Locations

The global configuration files and installed skill assets reside in the following platform-specific directories:

#### 🪟 Windows (PowerShell)
* **Configuration File (`opencode.json` / `opencode.jsonc`):**  
  `$env:USERPROFILE\.config\opencode\opencode.json`  
  *(Absolute: `C:\Users\<Your-Username>\.config\opencode\opencode.json`)*
* **Skill Storage Directory:**  
  `$env:USERPROFILE\.config\opencode\skills\dispatcher\`  
  *(Absolute: `C:\Users\<Your-Username>\.config\opencode\skills\dispatcher\`)*

#### 🐧 Linux & macOS (Bash)
* **Configuration File (`opencode.json` / `opencode.jsonc`):**  
  `~/.config/opencode/opencode.json`
* **Skill Storage Directory:**  
  `~/.config/opencode/skills/dispatcher/`

*(Note: Workspace-level configurations can also be placed directly in your project root as `./opencode.json` or `./.opencode/opencode.json`.)*

---

## ⚡ How to Trigger

1. Restart **OpenCode Desktop** to reload the cache.
2. Prefix your prompt with `/dispatch` in your chat workspace.

### Examples:
* **Complex Architecture:** `/dispatch I need to build a complex multi-screen Android application structure in Jetpack Compose`
* **Visual Bugs:** `/dispatch why is the layout alignment of my login screen padding broken?`
* **Boilerplate:** `/dispatch generate 15 simple unit tests for these data utilities`

---

## ⚙️ Core Architecture Details

When called, the engine executes a platform-native discovery sweep:
1. Triggers a live environmental refresh via `opencode models --refresh --verbose`.
2. Inspects performance metadata to strip away credit-consuming endpoints.
3. Automatically adapts if OpenCode updates add or drop base models over time.