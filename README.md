<div align="center">
  <img src="banner.jpg" alt="Agent Credit Saver Banner" width="100%">
  
  <h1>💸 Agent Credit Saver</h1>
  <p><b>Strict prompt guardrails to stop AI coding agents from burning your API credits.</b></p>
  
  [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
  [![Supports: Cursor](https://img.shields.io/badge/Supports-Cursor-black.svg)]()
  [![Supports: Claude Code](https://img.shields.io/badge/Supports-Claude_Code-d97757.svg)]()
  [![Supports: Windsurf](https://img.shields.io/badge/Supports-Windsurf-blue.svg)]()
  [![Supports: Antigravity](https://img.shields.io/badge/Supports-Antigravity-4285F4.svg)]()
</div>

## 🛑 The Problem: Why are you running out of credits?
Modern AI coding agents (Claude Code, Cursor, Windsurf, Copilot) are incredibly powerful, but they are **over-eager**. When you ask an agent to "fix a bug," it will often:

1. Run `npm run build` and ingest 10,000 lines of useless terminal output into its context.
2. Blindly search your repository (`grep`), burning thousands of input tokens.
3. Rewrite entire files just to change a single line of code.
4. Output a 500-word conversational summary of what it just did.

This behavior destroys your API budget, hits your daily usage limits, and leads to hallucinations.

## 💡 The Solution: "One File. Four Boundaries."
This repository contains a set of strict, drop-in system prompts that force your LLM into a **Token Diet**. By placing one of these hidden files in your project root, the AI is explicitly commanded to stop wasting tokens.

### The Guardrails:
1. **Compress Terminal Output:** Forces the agent to pipe raw logs to `/dev/null` or limit outputs (e.g., `head -n 20`).
2. **Anti-Blind-Search Protocol:** Stops the agent from running expensive global searches without looking at your architecture map first.
3. **Hot/Warm/Cold Tiering:** Forces the AI to only read full files if it's editing them.
4. **Stop When Finished:** Kills the "eager new hire" syndrome by banning long conversational summaries.

## 🚀 How to Install (Step-by-Step)

You do **not** need to download this entire repository to use the credit-saver guardrails! You just need to place a single text file into the root folder of your own coding project.

### Method 1: The One-Line Install (Recommended)
If you are already inside your project folder in the terminal, you can download the guardrail file directly into your project using one of the commands below. Choose the command for your specific AI agent:

**For Cursor:**
```bash
curl -o .cursorrules https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/.cursorrules
```

**For Claude Code:**
```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/CLAUDE.md
```

**For Windsurf:**
```bash
curl -o .windsurfrules https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/.windsurfrules
```

**For Google Antigravity:**
```bash
curl -o GEMINI.md https://raw.githubusercontent.com/CounterfietJoel/agent-credit-saver/master/templates/GEMINI.md
```

### Method 2: Manual Copy & Paste
1. Open your code project in your favorite editor.
2. Create a new file in the very top folder of your project (the root directory).
3. Name the file depending on what AI you use (e.g., `.cursorrules`, `CLAUDE.md`, `.windsurfrules`, or `GEMINI.md`).
4. Click into the [templates folder](https://github.com/CounterfietJoel/agent-credit-saver/tree/master/templates) in this repository, open the file you need, and copy/paste all the text inside into your new file.
5. Save the file. Your AI agent will automatically detect it the next time you ask it a question!

### Method 3: Start a New Project (GitHub Template)
If you are starting a brand new project and want to include these rules from day one:
👉 **Click the green "Use this template" button** at the top right of this repository to instantly create a new GitHub repository in your own account with all these guardrails pre-installed.

## 🧠 Advanced: Context Compression with Repomix
If you have a massive codebase, even these guardrails won't save you if you feed the agent too many files. We highly recommend using [Repomix](https://github.com/yamadashy/repomix) alongside these rules.

```bash
npx repomix
```
This packs your entire repository into a single, token-optimized XML file that maximizes **Prompt Caching** (which can reduce Anthropic/Gemini API costs by up to 90%).

## 🤝 Contributing & Remixing
If you find a prompt trick that saves even more tokens without degrading coding quality, open a Pull Request! Fork this repo, adapt it for your specific tech stack (e.g., adding strict Next.js or Python boundaries), and share it with the community.
