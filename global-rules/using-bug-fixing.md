# RULE 1: Bug Fix Protocol

**GOAL:** Systematically identify, research, and resolve bugs using evidence-based solutions.

**WHEN TO USE:** User reports error, linter shows issues, or tests fail.

---

## WORKFLOW

### 1. PLAN (Sequential Thinking)
- Use `mcp_server-sequential-thinking_sequentialthinking` to break down the bug investigation
- Map out: error location → root cause → potential solutions → validation strategy

### 2. LOCATE & UNDERSTAND
- **Find error:** exact file, line number, error message (use linter output or user report)
- **Read context:** use Serena's `mcp_serena_read_file` with line ranges to understand surrounding code
- **Trace symbols:** use `mcp_serena_find_symbol` and `mcp_serena_find_referencing_symbols` to understand dependencies

### 3. RESEARCH (MANDATORY - Never guess)
Execute in parallel when possible:

**A. Code Patterns (Priority 1)**
- `mcp_exa_get_code_context_exa`: search for error pattern + library name + "fix" to find working examples
- `mcp_octocode_githubSearchCode`: find proven fixes in high-star repos (≤3 keywords: e.g., "error", "fix", "library")

**B. Official Documentation**
- `mcp_context7_get_library_docs`: get authoritative docs for the library/framework causing the error

**C. Community Solutions**
- `mcp_brave_search_brave_web_search`: search for error message + context to find Stack Overflow discussions

**D. Full Context (if snippets insufficient)**
- `mcp_octocode_githubGetFileContent`: fetch complete working implementations from quality repos
- `mcp_octocode_githubViewRepoStructure`: explore repo structure to locate similar modules

### 4. FIX
- **Minimal change:** smallest edit that solves the bug, no refactoring
- **Use Serena editors:** `mcp_serena_replace_regex` or `mcp_serena_replace_symbol_body`
- **Preserve style:** match existing code patterns exactly

### 5. VERIFY
- **Lint check:** `read_lints` on modified file
- **Run tests:** if available, execute relevant test suite
- **Confirm:** explain change and how to verify

---

## MCP TOOL QUICK REFERENCE

| Need | Tool | Usage |
|------|------|-------|
| Plan approach | `sequential-thinking` | Break down investigation |
| Read code | `serena_read_file` | Targeted line ranges |
| Find symbol | `serena_find_symbol` | Locate definitions |
| Trace usage | `serena_find_referencing_symbols` | Find callers |
| Code examples | `exa_get_code_context` | Real-world patterns |
| GitHub search | `octocode_githubSearchCode` | Proven fixes |
| Full files | `octocode_githubGetFileContent` | Complete implementations |
| Official docs | `context7_get_library_docs` | Authoritative reference |
| Community help | `brave_web_search` | Stack Overflow, blogs |
| Edit code | `serena_replace_*` | Minimal changes |

---

## VALIDATION CHECKLIST
- [ ] Error location identified (file, line, message)
- [ ] Root cause understood via symbol tracing
- [ ] Research completed (≥2 sources: code examples + docs)
- [ ] Solution validated against proven patterns
- [ ] Minimal change applied (no refactoring)
- [ ] Linter passes
- [ ] Fix explained with reasoning
