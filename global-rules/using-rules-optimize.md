# RULE 2: MANDATORY RULES FOR USING EXACT TOOL FOR EFFECTIVE CODE EDITING/CODE FIXING
_(PHASE 2 of 3: IMPLEMENTATION)_

**When use this rule ?**:  when code, make sure follow all the instruction below

Strategic tool selection for fast code exploration → precise editing → efficient maintenance

---

## CORE PHILOSOPHY: INTELLIGENT TOOL SELECTION

**GUIDING PRINCIPLE:** Start broad, then go deep. Prioritize speed for exploration and precision for modification.

**GOAL:** Maximize code understanding speed + precision while minimizing token usage through smart tool selection.

---

## TOOL SELECTION MATRIX

### CODE EXPLORATION & UNDERSTANDING

**CURSOR FIRST for Fast Discovery:**
- `codebase_search`: High-level architecture understanding, concept exploration.
- `list_dir`: Project structure overview.
- `file_search`: Find files by name/pattern.
- `grep`: Quick literal text/pattern matching across the codebase.

**SERENA for Symbol-Level Precision:**
- `find_symbol`: Locate specific functions/classes with LSP accuracy.
- `get_symbols_overview`: Understand a file's symbol structure without reading its content.
- `find_referencing_symbols`: Trace dependencies and usage across the codebase.
- `search_for_pattern`: Flexible regex-based pattern search when `grep` is insufficient.

### CODE EDITING & MODIFICATION

**SERENA for Surgical Precision:**
- `replace_symbol_body`: Replace entire functions/classes. Language-aware and safe.
- `insert_after_symbol` / `insert_before_symbol`: Precisely add new code blocks or symbols.
- `replace_regex`: **For small, intra-symbol changes.** The most token-efficient method for minor edits within a function or block.
- **Preferred for:** All symbol-level changes, language-aware edits, and token-efficient minor modifications.

**CURSOR for Bulk/Multi-Location Operations:**
- `edit_file`: Apply multiple, non-symbol-aware changes across a single file using `// ... existing code ...` syntax.
- **Preferred for:** Refactoring tasks involving many small, scattered text changes within one file.

### KNOWLEDGE MANAGEMENT

**SERENA Memory System:**
- `write_memory`: Store project insights for future sessions
- `read_memory`: Recall previous learnings
- `list_memories`: Check available knowledge

---

## THE UNIVERSAL CODING WORKFLOW
A 4-phase approach to any coding task, from new features to bug fixes.

### PHASE 1: EXPLORATION & DISCOVERY (CURSOR-FIRST)
**Goal:** Gain high-level context and locate relevant areas quickly.
**Principle:** Speed over Precision.
1.  **`list_dir` & `read_file` (on metadata files):** Understand project structure, dependencies (`package.json`, `requirements.txt`), and setup (`README.md`).
2.  **`codebase_search` (Semantic Questions):** Ask high-level questions like `"How is user authentication handled?"` or `"Where are API routes defined?"` to find key files and modules.
3.  **`grep` (Keyword Search):** Use for quick searches of specific variable names, error messages, or keywords if their exact location is unknown.
4.  **Serena Think Checkpoint:** Call `mcp_serena_think_about_task_adherence` to verify the exploration path, and `mcp_serena_think_about_collected_information` to ensure gathered context is sufficient before deep analysis.

### PHASE 2: DEEP ANALYSIS & PLANNING (SERENA-FIRST)
**Goal:** Understand specific code paths, dependencies, and impact with perfect accuracy before making any changes.
**Principle:** Precision over Speed.
1.  **`get_symbols_overview`:** On key files identified in Phase 1, get a "table of contents" of all classes and functions without reading the code.
2.  **`find_symbol`:** Pinpoint the exact location of the target class or function you need to analyze or modify.
3.  **`find_referencing_symbols` (CRITICAL SAFETY CHECK):** Before planning any edit, find all usages of the target symbol. This is mandatory to understand the full impact of a change.

### PHASE 3: SURGICAL IMPLEMENTATION (RIGHT-TOOL-FOR-THE-JOB)
**Goal:** Modify code with maximum efficiency, precision, and token-safety.
**Method:** Choose the tool that best fits the scale of the change.
-   **To Replace an Entire Function/Class:** Use `mcp_serena_replace_symbol_body`.
-   **To Add a New Function/Class:** Use `mcp_serena_insert_after_symbol` or `insert_before_symbol`.
-   **To Change 1-5 Lines Inside a Function:** Use `mcp_serena_replace_regex` with wildcards (`.*?`) for maximum token efficiency. This is the preferred method for small modifications.
-   **To Make Multiple Small, Scattered Edits in One File:** Use Cursor's `edit_file`.
 -   **Serena Think Gate (Before Edit):** Re-run `mcp_serena_think_about_task_adherence` to confirm scope, impacted symbols, and rollback plan.

### PHASE 4: VALIDATION & KNOWLEDGE CAPTURE (POST-MODIFICATION GATE)
**Goal:** Ensure code integrity and persist learnings for future tasks.
**Principle:** Trust but Verify.
1.  **`read_lints` (MANDATORY):** After every file modification, run this tool on the changed file to catch any introduced syntax or quality errors.
2.  **`mcp_serena_write_memory`:** If you discovered important architectural patterns, business logic, or gotchas, save this knowledge to a memory file (e.g., `project-overview`, `architecture-patterns`).
3.  **Serena Think Retrospective:** Use `mcp_serena_think_about_whether_you_are_done` to verify completion criteria and identify follow-ups.

---

## EFFICIENCY RULES

### DO:
- **Parallel Execution:** Run multiple read-only tools simultaneously
- **Strategic Reading:** Use `read_file` with offset/limit for large files
- **Memory First:** Check `mcp_serena_read_memory()` before re-discovery
- **Symbol-First:** Prefer symbol-based operations over line-based when possible
- **Context Validation:** Confirm understanding before making changes

### DON'T:
- Read entire large files without exploring first.
- Use `codebase_search` for exact symbol names (use `mcp_serena_find_symbol`).
- Use `mcp_serena_replace_symbol_body` for a single-line change inside a function (use `mcp_serena_replace_regex` instead).
- Ignore Serena memory system for knowledge persistence.
- Make assumptions without validation.

---

## DECISION LOGIC

### When to use CURSOR:
- Primarily in **Phase 1** for initial codebase exploration and high-level understanding.
- For fast text/pattern searching across the entire project (`grep`).
- For applying multiple, non-symbol-aware edits within a single file (`edit_file`).

### When to use SERENA MCP:
- Primarily in **Phase 2 & 3** for high-precision analysis and modification.
- When you need to understand or edit code based on its structure (symbols), not just its text.
- For all cross-file reference analysis.
- For token-efficient, surgical code edits (`replace_regex`).
- For knowledge persistence across sessions.

### When to use BOTH:
- Complex feature implementation
- Comprehensive refactoring
- Bug investigation across multiple files
- Learning new codebase patterns

---

## QUALITY GATES

### Before Any Code Changes:
- Full context understanding achieved
- Dependencies and references mapped
- Impact scope assessed
- Appropriate tool selected for precision level needed

### After Code Changes:
- `read_lints()` validation completed
- Changes tested if possible
- Knowledge updated in Serena memory
- Documentation updated if needed

---

## SUCCESS METRICS

**You're succeeding when:**
- Understanding codebase faster than reading everything
- Making precise changes without breaking dependencies
- Maintaining context across work sessions
- Minimizing redundant operations and token usage
- Leveraging both tool ecosystems optimally

**You're failing when:**
- Reading entire large files without targeted exploration
- Using wrong tool for the task (precision vs speed)
- Ignoring available memory/knowledge
- Making changes without understanding impact
- Redundant operations across different tools

---

## QUICK REFERENCE

### Task Types and Tool Selection:

**Task Type: Explore Unknown Code**
- **Primary Tool:** Cursor `codebase_search`
- **Secondary Tool:** Serena symbols
- **Key Principle:** Fast → Precise

**Task Type: Find Specific Symbol**
- **Primary Tool:** Serena `find_symbol`
- **Secondary Tool:** Cursor `grep`
- **Key Principle:** Precision first

**Task Type: Understand Dependencies**
- **Primary Tool:** Serena `find_referencing`
- **Secondary Tool:** Cursor `codebase_search`
- **Key Principle:** Symbol-level accuracy

**Task Type: Bulk Text Changes**
- **Primary Tool:** Cursor `MultiEdit`
- **Secondary Tool:** Serena regex
- **Key Principle:** Efficiency for scale

**Task Type: Surgical Code Edits**
- **Primary Tool:** Serena symbol tools
- **Secondary Tool:** None
- **Key Principle:** Language-aware precision

**Task Type: Knowledge Management**
- **Primary Tool:** Serena memory
- **Secondary Tool:** None
- **Key Principle:** Persistence across sessions
