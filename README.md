# 🧠 opencode-advisor

An intelligent model recommendation engine for OpenCode that analyzes your tasks and points you to the best active free / Zen-tier model.

---

## ⚠️ Important Prerequisite

OpenCode evaluates prompts and skills **using your currently active model**.

To prevent errors when triaging multimodal tasks (such as screenshots or UI mockups), **set a lightweight multimodal/vision-capable model as your default model** in OpenCode. If your active model is text-only, it will reject image attachments before the advisor can evaluate them.

---

## 🛠️ Installation

Clone the repository into your OpenCode skills directory:

### 🪟 Windows (PowerShell)
```powershell
git clone https://github.com/tempius/opencode-advisor.git "$env:USERPROFILE\.config\opencode\skills\advisor"
```

### 🐧 Linux & macOS (Bash)
```bash
git clone https://github.com/tempius/opencode-advisor.git ~/.config/opencode/skills/advisor
```

---

## ⚡ How to Use

1. Restart **OpenCode Desktop** (or reload skills).
2. Prefix your prompt with `/advisor`:

### Example Workflow
```text
User:
/advisor I need to diagnose UI layout padding issues from this screenshot.

Advisor:
🛰️ Telemetry Status: Model Recommendation Ready
* Recommended Model: opencode/muse-spark-1.2-contributor-free
* Operational Mode: Visual UI Debugging
* Selection Rationale: Multimodal free model supporting direct image analysis and deep reasoning.

📋 Switch Instructions:
* Interactive UI / TUI: Type /models and select muse-spark-1.2-contributor-free
* CLI Session: opencode -m muse-spark-1.2-contributor-free
```

---

## ⚙️ Core Architecture

When invoked, the advisor:
1. Executes `opencode models --refresh --verbose` via dynamic tool inspection.
2. Identifies free/zen-tier nodes (0.0 credit cost).
3. Matches your task requirements (reasoning depth, tool-use execution, throughput speed, or vision/multimodal parsing) to the optimal model.