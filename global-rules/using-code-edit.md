# Rule 4: Rule for Code Analysis and Editing by using Serena MCP and Cursor's built in tools

## Core Mindset
- Investigate first, edit second; prioritize understanding over speed.
- Communicate concisely; surface uncertainties early; never guess silently.
- Keep changes minimal and reversible; avoid unrelated refactors/formatting churn.

## Investigation Workflow
1. **Session Prep**
   - Serena: `activate_project`; `list_memories` → read relevant entries; note anything stale.
2. **Bird’s‑Eye Map**
   - Cursor: Explorer for fast tree; Codebase search for high-level topics/features.
   - Serena: `list_dir` (recursive when needed) to capture a structured map programmatically.
3. **Symbol Navigation**
   - Serena: `get_symbols_overview` on key files to learn available classes/functions.
   - Serena: `find_symbol` to locate exact definitions; record file paths.
4. **Relationship Mapping**
   - Serena: `find_referencing_symbols` to learn who calls/uses a symbol; note upstream/downstream.
5. **Targeted Reading**
   - Cursor: open files for quick skim and navigation.
   - Serena: `read_file` with `start_line`/`end_line` (as strings) for precise, quotable slices.
6. **Clarify Gaps**
   - If requirements/architecture remain unclear, pause and ask before planning edits.

## Editing Guardrails
- Confirm acceptance criteria and summarize your plan before modifying code.
- Choose the smallest effective Serena editor:
  - `replace_regex` for 1–5 line localized tweaks inside a symbol.
  - `insert_before_symbol` / `insert_after_symbol` to add adjacent helpers or config.
  - `replace_symbol_body` for full function/class rewrites.
- Mirror existing style/patterns; do not reformat unrelated code.
- Cursor: use Diff viewer to review and stage chunks cleanly before handing back.

## Validation & Communication
- After each edit: use Cursor Diagnostics/Problems to fix errors immediately.
- Use terminal with non-interactive flags; append `| cat` to avoid pagers.
- Summarize what changed, why it solves the request, risks, and next steps (tests/commits).

## Task-to-Tool Matrix (Cursor ↔ Serena)
- **Repository mapping**
  - Cursor: Explorer for visual overview; Codebase search to orient by feature/topic.
  - Serena: `list_dir` for recursive, filtered, reproducible maps.
- **Search by text/symbol**
  - Cursor: Search/Grep panel for exact strings, regex, filenames; fastest confirmation.
  - Serena: `find_symbol` for declarations; `find_referencing_symbols` for callers across files.
- **Semantic discovery**
  - Cursor: Codebase search for concepts and feature names.
  - Serena: `get_symbols_overview` → convert concepts to concrete symbols, then `read_file`.
- **Reading code**
  - Cursor: navigate broadly in-editor.
  - Serena: `read_file` line ranges for minimal context window and precise citations.
- **Planning changes**
  - Cursor: draft plan in a scratch doc; preview with Diff.
  - Serena: `think_about_collected_information` and `think_about_task_adherence` to gate edits.
- **Applying edits**
  - Serena: `replace_regex`, `insert_*`, `replace_symbol_body` for precise, auditable edits.
  - Cursor: Diff viewer + Git staging to present and commit changes.
- **Validation & linting**
  - Cursor: Diagnostics/Problems; run tests/linters via terminal (non-interactive flags).
  - Serena: optional verification reads (`read_file`) to confirm applied code in place.
- **Documentation & references**
  - Cursor: Web panel for docs/examples (prefer official sources); save links if needed.
  - Serena: memories to persist architecture decisions and recurring patterns.

## Octocode MCP — External code discovery and retrieval
- Purpose: Retrieve high-quality, real-world code from GitHub to complement Exa patterns.
- When to use:
  - Need full files (not just snippets) for end-to-end understanding.
  - Need to inspect repository structure to locate key modules.
  - Need exemplars from reputable repositories (by stars/topics) before implementation.
- Tools:
  - `mcp_octocode_githubViewRepoStructure`: explore repository tree to find `src/`, `app/`, or entry points.
  - `mcp_octocode_githubSearchCode`: search for code with ≤3 focused keywords; filter by `filename`, `path`, `language`, `stars` as needed.
  - `mcp_octocode_githubGetFileContent`: fetch entire files or specific line ranges for precise context.
  - `mcp_octocode_githubSearchRepositories`: discover high-quality repositories to source examples.
- Practices:
  - Start broad, then narrow with `filename`/`path` filters.
  - Run multiple focused searches in parallel rather than a single broad query.
  - Cite existing code using CODE REFERENCES format: `startLine:endLine:filepath`.

## Tool Companion Sheet
- **Serena Essentials**
  - Discovery: `list_dir`, `get_symbols_overview`, `find_symbol`, `find_referencing_symbols`, `read_file`.
  - Editing: `replace_regex`, `insert_before_symbol`, `insert_after_symbol`, `replace_symbol_body`.
  - Meta-thinking: `think_about_collected_information`, `think_about_task_adherence`, `think_about_whether_you_are_done`.
- **Cursor Built-ins**
  - Explorer (list directory), Search/Grep panel, Codebase search, Diff viewer, Diagnostics/Problems, Terminal (append `| cat`), Web.
- Default: use Serena for structured analysis/edits; use Cursor to navigate, visualize, validate, and present results efficiently.
