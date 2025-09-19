# RULE 1: Code Editing Rules

Goal: Always understand the current code context before editing. Combine Serena’s semantic, symbol-level tools with Cursor’s built-ins. Edit only after scope and impact are clear.

- Understand before you edit
  - Clarify intent: what to add/change, acceptance criteria, constraints.
  - Load context fast:
    - Cursor built-ins: project search (exact/regex), open key files, diagnostics/problems, Git diff/staging.
    - Serena analysis:
      - get_symbols_overview on relevant files (top-level symbols).
      - find_symbol to locate exact functions/classes.
      - find_referencing_symbols to map impact and call sites.
      - search_for_pattern for non-symbol patterns (configs/strings).
      - list_dir/read_file to inspect structure and source selectively.
      - read_memory/list_memories to reuse knowledge; write_memory to save new insights.
    - External Pattern Research (OctoCode):
      - For complex or unfamiliar patterns, use OctoCode MCP to find real-world implementations on GitHub, providing broader context.
  - Confirm understanding: current behavior, inputs/outputs, side effects, error paths, involved tests/configs.

- Plan minimal, safe changes
  - Choose the right tool:
    - Single, small line tweaks inside a symbol → Serena replace_regex.
    - Replace an entire function/class → Serena replace_symbol_body.
    - Add code adjacent to a symbol → Serena insert_after_symbol / insert_before_symbol.
    - Many small scattered edits in one file → Cursor multi-location edit.
    - Exact string lookups → Cursor search/grep; large semantic discovery → Serena tools.
  - Prefer early returns, clear names, single-responsibility functions (<30 lines when possible).

- Execute with guardrails
  - Make small, verifiable edits; avoid unrelated changes.
  - After each edit:
    - Run lints (read_lints) and fix immediately.
    - Run tests/build if available; inspect failures; iterate.
  - Update memories (write_memory) with architecture/context you discovered.

- Impact verification (must-pass)
  - All references accounted for (find_referencing_symbols shows no misses).
  - Error handling and edge cases covered; types/interfaces consistent across boundaries.
  - Tests and lints pass; no obvious performance regressions.

- When uncertain
  - Ask for clarification on ambiguous requirements or missing constraints before editing.
  - If the codebase is tiny and symbol tools add overhead, prefer Cursor built-ins; otherwise default to Serena’s symbol flow.

- Tool quick map (when to use)
  - Serena (semantic/symbol): get_symbols_overview, find_symbol, find_referencing_symbols, search_for_pattern, insert_* / replace_symbol_body / replace_regex, read_memory/write_memory/list_memories, list_dir, read_file.
  - Cursor (built-ins): project search (exact/regex), file navigation, diagnostics/quick-fixes, Git diff/stage/commit.
  - OctoCode (external research): githubSearchCode, githubViewRepoStructure for finding real-world implementation patterns.

- Editing tool policy
  - It is OK to perform edits with Cursor built-ins (multi-location edits, quick exact changes).
  - Use Serena's editing tools for symbol-scoped changes when precision/traceability matters (replace_symbol_body, insert_*, replace_regex).
  - Regardless of tool choice, follow Change control & traceability and show diffs.

- Success criteria
  - You can explain current behavior and precisely what changes are needed before touching code.
  - Edits are minimal, symbol-aware, and pass lints/tests.
  - Memory updated so future tasks start faster.

- Defaults & safety
  - Do not edit before context is understood; keep changes scoped; use Git for reviewability.
  - Prefer Serena for large/complex refactors; prefer Cursor for quick exact matches or tiny changes.
- Change control & traceability (must-do)
  - Before editing: state target symbols/files and intended operations (add/remove/modify) and why.
  - Use symbol-scoped edits:
    - insert_before_symbol / insert_after_symbol (add adjacent code)
    - replace_symbol_body (full function/class replacement)
    - replace_regex (1–5 line local tweak)
  - Keep edits small and atomic; one logical change per edit.
  - Always show exact diffs after each edit:
    - Cite code with file path and lines (before → after) using Cursor’s Git diff.
    - If multiple files, commit per-file or per-change-set with clear messages.
  - After editing: summarize what changed and why; update memories with key decisions.
  - If uncertainty remains, stop and request confirmation before proceeding further.
