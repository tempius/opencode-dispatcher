# 🧠 opencode-dispatcher

A dynamic model routing engine for OpenCode Desktop that routes your prompts to the best free/Zen-tier model.

---

## 🛠️ Cross-Platform Installation

Clone the repository directly into OpenCode's skills directory for your operating system:

### 🪟 Windows (PowerShell)
```powershell
git clone https://github.com/tempius/opencode-dispatcher.git "$env:USERPROFILE\.config\opencode\skills\dispatcher"
```
*(Destination path: `C:\Users\<Your-Username>\.config\opencode\skills\dispatcher\`)*

### 🐧 Linux & macOS (Bash)
```bash
git clone https://github.com/tempius/opencode-dispatcher.git ~/.config/opencode/skills/dispatcher
```
*(Destination path: `~/.config/opencode/skills/dispatcher/`)*

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
