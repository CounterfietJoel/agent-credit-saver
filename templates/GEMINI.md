# GLOBAL AI EFFICIENCY RULES (CREDIT SAVER)

You are operating under strict token-efficiency, context-hygiene, and cost-reduction constraints. You MUST strictly follow these boundaries on every turn:

## 1. Surgical Edits & Zero Boilerplate
* **Write targeted edits:** Never rewrite an entire file to change a few lines. Always use unified diffs, targeted line replacements, or surgical chunk edits where available.
* **No speculative code:** Never add unrequested features, speculative helper utilities, or boilerplate comments.
* **Confirm ambiguity:** If requirements are underspecified or ambiguous, stop and ask the user directly rather than guessing and generating wasted output.

## 2. Cross-Platform Terminal Output Compression
When executing terminal commands (e.g., package managers, builds, test suites, git commands), you MUST prevent massive stdout/stderr logs from polluting the context window:
* **Silence successful verbose commands:**
  - Linux/macOS (Bash/Zsh): `command > /dev/null 2>&1`
  - Windows (PowerShell): `command | Out-Null`
  - Windows (CMD): `command > nul 2>&1`
* **Limit output length:**
  - Linux/macOS: `command | head -n 20` or `command | tail -n 20`
  - Windows (PowerShell): `command | Select-Object -First 20` or `command | Select-Object -Last 20`
* **Error handling:** If a build or test fails, extract and inspect ONLY the relevant error messages and stack traces, never whole verbose logs.

## 3. Anti-Blind-Search Protocol
* Always inspect root architectural files (`README.md`, `package.json`, directory maps) before running global search tools.
* **Scope all searches:** Constrain searches (`grep`, `find`) to specific subdirectories or file extensions.
* **Exclude vendor & build dirs:** NEVER run unconstrained recursive searches across `node_modules`, `dist`, `build`, `.next`, `target`, `.git`, or vendor cache directories.

## 4. Hot / Warm / Cold Context Tiering
* **HOT (Full Read):** Read the full file contents ONLY for files you actively plan to edit.
* **WARM (Interface Only):** For dependencies, helper modules, or imports, view ONLY type signatures, function headers, or top-level exports.
* **COLD (Ignore):** Completely ignore unrelated modules and assets.

## 5. Zero-Fluff Responses
* Keep conversational text extremely brief (1–2 sentences maximum upon completion).
* NEVER output long conversational preamble or post-task summaries unless explicitly asked.
