# 🧠 opencode-picker

An intelligent model recommendation engine for OpenCode that analyzes your tasks and points you to the best active free / Zen-tier model.

---

## ⚠️ Important Prerequisite

OpenCode evaluates prompts and skills **using your currently active model**.

To prevent errors when triaging multimodal tasks (such as screenshots or UI mockups), **set a lightweight multimodal/vision-capable model as your default model** in OpenCode. If your active model is text-only, it will reject image attachments before the picker can evaluate them.

---

## 🛠️ Installation

Clone the repository into your OpenCode skills directory:

### 🪟 Windows (PowerShell)
```powershell
git clone https://github.com/tempius/opencode-picker.git "$env:USERPROFILE\.config\opencode\skills\picker"
```

### 🐧 Linux & macOS (Bash)
```bash
git clone https://github.com/tempius/opencode-picker.git ~/.config/opencode/skills/picker
```

---

## ⚡ How to Use

1. Restart **OpenCode Desktop** (or reload skills).
2. Prefix your prompt with `/picker`:

### Example Workflow
```text
User:
/picker I need to diagnose UI layout padding issues from this screenshot.

Picker:
🛰️ Telemetry Status: Model Recommendation Ready
* Recommended Model: opencode/muse-spark-1.2-contributor-free
* Operational Mode: Visual UI Debugging
* Specs & Tier: Zen (Free) | Multimodal | Deep Reasoning
* Selection Rationale: Multimodal free model supporting direct image analysis and layout reasoning.

📋 Switch Instructions:
* Interactive UI / TUI: Type `/model` and select `muse-spark-1.2-contributor-free`
* CLI Session (One-Liner): `opencode -m opencode/muse-spark-1.2-contributor-free "Analyze the attached screenshot to diagnose and fix the UI layout padding issues."`

💡 Suggested Next Prompt:
```text
Analyze the attached screenshot to diagnose and fix the UI layout padding issues.
```
```

---

## ⚙️ Core Architecture

When invoked, the picker:
1. Executes `opencode models --refresh --verbose` via dynamic tool inspection.
2. Identifies active free/zen-tier nodes (0.0 credit cost) with automatic fallback handling.
3. Matches your workload (reasoning depth, tool-use loops, throughput, large-context audits, or multimodal vision) to the optimal model.
4. Generates switch commands and a refined prompt ready for immediate execution.