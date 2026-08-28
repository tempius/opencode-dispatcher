\# 🧠 opencode-dispatcher



A dynamic model routing engine for OpenCode Desktop. It automatically queries your active infrastructure cache via the CLI, filters out premium models, and triages your prompts to the absolute best \*\*free / Zen-tier\*\* model for the job.



\## 🛠️ Cross-Platform Installation



Choose the setup instructions corresponding to your operating system to place the skill into OpenCode's global configuration directory.



\### 🪟 Windows (PowerShell)

```powershell

\# 1. Create the skill directory structure

mkdir -p "$env:USERPROFILE\\.config\\opencode\\skills\\dispatcher"



\# 2. Download the skill straight into your local configuration directory

Invoke-WebRequest -Uri "https://raw.githubusercontent.com/YOUR\_USERNAME/opencode-dispatcher/main/SKILL.md" -OutFile "$env:USERPROFILE\\.config\\opencode\\skills\\dispatcher\\SKILL.md"

```



\### 🐧 Linux \& macOS (Bash)

```bash

\# 1. Create the skill directory structure

mkdir -p \~/.config/opencode/skills/dispatcher



\# 2. Download the skill straight into your local configuration directory

curl -sSL "https://raw.githubusercontent.com/YOUR\_USERNAME/opencode-dispatcher/main/SKILL.md" -o \~/.config/opencode/skills/dispatcher/SKILL.md

```



\---



\## ⚡ How to Trigger



1\. Completely \*\*restart OpenCode Desktop\*\* to flush the skill engine cache.

2\. In any project workspace chat, prefix your instructions with the `/dispatch` keyword to let the triage layer route your prompt dynamically:



```text

/dispatch I need to build a complex multi-screen Android application structure in Jetpack Compose

```



\## ⚙️ Core Architecture Details



When called, the engine executes a platform-native discovery sweep:

1\. Triggers an live environmental refresh via `opencode models --refresh --verbose`.

2\. Inspects performance metadata to strip away credit-consuming endpoints.

3\. Automatically adapts if OpenCode updates add or drop base models over time.



