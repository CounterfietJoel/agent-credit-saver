<div align="center">
  <img src="banner.jpg" alt="Agent Credit Saver Banner" width="100%">
  
  <h1>💸 Agent Credit Saver</h1>
  <p><b>Strict prompt guardrails to stop AI coding agents from burning your API credits & token budgets.</b></p>
  
  [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
  [![Supports: Cursor](https://img.shields.io/badge/Supports-Cursor-black.svg)]()
  [![Supports: Claude Code](https://img.shields.io/badge/Supports-Claude_Code-d97757.svg)]()
  [![Supports: Windsurf](https://img.shields.io/badge/Supports-Windsurf-blue.svg)]()
  [![Supports: Google Antigravity](https://img.shields.io/badge/Supports-Google_Antigravity-4285F4.svg)]()
  [![Prompt Caching: Optimized](https://img.shields.io/badge/Prompt_Caching-Optimized-brightgreen.svg)]()
</div>

---

## 🛑 The Problem: Why are you running out of credits?
Modern AI coding agents (Google Antigravity, Claude Code, Cursor, Windsurf, GitHub Copilot) are remarkably capable, but unconstrained agents are **over-eager token spenders**. When you ask an agent to "fix a bug," it will often:

1. **Dump massive terminal output into context:** Running `npm run build`, test suites, or git logs and ingesting 10,000+ lines of raw console logs.
2. **Blindly search your codebase:** Running unconstrained global `grep` / `find` across entire repositories (including `node_modules`, `dist`, `.next`, and build artifacts).
3. **Rewrite entire files:** Overwriting a 1,000-line file just to modify a 2-line conditional.
4. **Produce conversational fluff:** Outputting 500-word summaries explaining what it just did, burning expensive output tokens on every turn.

This behavior rapidly depletes your token budgets, triggers rate limits, increases latency, and degrades model reasoning due to context pollution ("context rot").

---

## 💡 The Solution: "One File. Five Boundaries."
This repository provides lean, zero-overhead, drop-in system guardrail files that put your agent on a strict **Token Diet**. By placing one rule file in your project root, your coding agent is strictly constrained from wasting tokens.

### The 5 Guardrails:
1. **Surgical Edits & Zero Boilerplate:** Mandates targeted line replacements or unified diffs instead of full-file rewrites. Forbids unrequested speculative code.
2. **Cross-Platform Terminal Output Compression:** Enforces output silencing (`/dev/null` or `Out-Null`) and log clipping (`head -n 20` or `Select-Object -First 20`) on Windows, Linux, and macOS.
3. **Anti-Blind-Search Protocol:** Requires checking architectural root maps before searching, and bans searches in build/vendor directories (`node_modules`, `dist`, `build`, `.git`).
4. **Hot / Warm / Cold Tiering:** Restricts full-file reads strictly to files being edited (`HOT`), using interface/symbol signatures only for dependencies (`WARM`), and ignoring unrelated files (`COLD`).
5. **Zero-Fluff Responses:** Eliminates conversational padding and forces 1–2 sentence completion summaries to preserve output tokens.

---

## 🚀 How to Install (Step-by-Step)

You do **not** need to clone this repository to use the guardrails. Simply drop a single rule file into the root folder of your project.

### Method 1: The One-Line Terminal Install

#### 🌐 Linux / macOS (Bash / Zsh):
```bash
# For Google Antigravity / Gemini CLI:
curl -o .geminirules https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/.geminirules

# For Cursor:
curl -o .cursorrules https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/.cursorrules

# For Claude Code:
curl -o CLAUDE.md https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/CLAUDE.md

# For Windsurf:
curl -o .windsurfrules https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/.windsurfrules
```

#### 🪟 Windows (PowerShell):
```powershell
# For Google Antigravity / Gemini CLI:
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/.geminirules" -OutFile ".geminirules"

# For Cursor:
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/.cursorrules" -OutFile ".cursorrules"

# For Claude Code:
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/CLAUDE.md" -OutFile "CLAUDE.md"

# For Windsurf:
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/.windsurfrules" -OutFile ".windsurfrules"
```

---

### Method 2: Manual Copy & Paste
1. Open your project in your code editor.
2. In the root directory of your project, create the appropriate rule file:
   - Google Antigravity: `.geminirules` or `GEMINI.md`
   - Cursor: `.cursorrules`
   - Claude Code: `CLAUDE.md`
   - Windsurf: `.windsurfrules`
3. Copy the contents of [`templates/base-rules.md`](templates/base-rules.md) and paste it into your new file.
4. Save the file. Your AI agent will automatically detect and enforce it on its next prompt!

---

### Method 3: Start a New Project (GitHub Template)
If you are starting a brand new project and want pre-installed guardrails:
👉 **Click the green "Use this template" button** at the top right of this repository to create a fresh repository with all rules built-in.

---

## ⚡ Prompt Caching & Token Economics

Modern LLMs (including **Google Gemini 2.0 / 1.5** and **Anthropic Claude 3.5 / 3.7**) offer **Prompt Caching** discounts of up to **90%** on input tokens when the prompt prefix remains consistent.

```
┌──────────────────────────────────────────────────────────┐
│  Static Rule Prefix (.geminirules / CLAUDE.md)          │ ──► CACHED (~90% Cost Reduction)
├──────────────────────────────────────────────────────────┤
│  Hot / Warm Surgical File Context (Targeted Diffs)       │ ──► Dynamic Input
├──────────────────────────────────────────────────────────┤
│  1-2 Sentence Direct Code Output                         │ ──► Minimal Output Tokens
└──────────────────────────────────────────────────────────┘
```

By maintaining standard, concise rules in your project root:
- The system instructions stay **stable across turns**, triggering prompt cache hits.
- Suppressing verbose terminal logs prevents cache invalidation and context churn.
- Banning full-file rewrites saves massive input/output token volume per turn.

---

## 🧠 Advanced: Context Compression with Repomix

For large codebases, pair these rules with [Repomix](https://github.com/yamadashy/repomix) to generate compact, token-optimized context packs:

```bash
npx repomix
```

This compiles your repository into a single, structured XML context map that maximizes prompt cache efficiency.

---

## 🤝 Contributing & Customization

Have a domain-specific optimization or prompt trick for specific stacks (e.g., Python, Rust, Next.js, Kubernetes)? 
* Open a Pull Request or create specialized templates in `templates/`!
* Fork this repository to tailor rules for your team's internal workflows.

## 📄 License
MIT © [CounterfietJoel](https://github.com/CounterfietJoel)
