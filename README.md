<div align="center">
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

## 🚀 Quick Start (Use as a Template)

GitHub's equivalent of "Remixing" is **Forking** and **Templates**. 

👉 **[Click "Use this template"](#)** at the top of this repository to instantly copy these guardrails into your own GitHub account, or simply copy the file for your specific AI editor into the root of your project:

*   **For Cursor:** Copy `templates/base-rules.md` to `.cursorrules`
*   **For Claude Code:** Copy `templates/base-rules.md` to `CLAUDE.md`
*   **For Windsurf:** Copy `templates/base-rules.md` to `.windsurfrules`
*   **For Google Antigravity:** Copy `templates/base-rules.md` to `GEMINI.md`

## 🧠 Advanced: Context Compression with Repomix
If you have a massive codebase, even these guardrails won't save you if you feed the agent too many files. We highly recommend using [Repomix](https://github.com/yamadashy/repomix) alongside these rules.

```bash
npx repomix
```
This packs your entire repository into a single, token-optimized XML file that maximizes **Prompt Caching** (which can reduce Anthropic/Gemini API costs by up to 90%).

## 🤝 Contributing & Remixing
If you find a prompt trick that saves even more tokens without degrading coding quality, open a Pull Request! Fork this repo, remix it for your specific tech stack (e.g., adding strict Next.js or Python boundaries), and share it with the community.

## SEO Keywords (For Discoverability)
`AI Agent`, `Claude Code`, `Cursor AI`, `Windsurf IDE`, `Token Optimization`, `Save API Credits`, `LLM Prompt Caching`, `Agentic Workflow`, `Reduce AI Costs`, `.cursorrules`, `Anthropic`.
