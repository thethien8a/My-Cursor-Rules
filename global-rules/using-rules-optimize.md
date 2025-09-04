# RULE 2: MANDATORY RULES FOR EFFECTIVE CODING:

*Strategic tool selection for fast code exploration → precise editing → efficient maintenance*

## CORE PHILOSOPHY: INTELLIGENT TOOL SELECTION

**GOAL:** Maximize code understanding speed + precision while minimizing token usage through smart tool selection.

**INTEGRATION WITH OTHER RULES:**
- Rule 1 takes precedence for analysis phase (research planning)
- Rule 3 takes precedence for memory operations
- Sequential-thinking is primarily for Rule 1 research planning
- Use regular thinking patterns for coding workflows

---

## TOOL SELECTION MATRIX

### CODE EXPLORATION & UNDERSTANDING

**CURSOR FIRST for Fast Discovery:**
```
- codebase_search: High-level architecture understanding, concept exploration
- list_dir: Project structure overview
- file_search: Find files by name/pattern
- grep_search: Quick text/pattern matching across codebase
```

**SERENA for Symbol-Level Precision:**
```
- find_symbol: Locate specific functions/classes with LSP accuracy
- get_symbols_overview: Understand file's symbol structure
- find_referencing_symbols: Trace dependencies and relationships
- search_for_pattern: Flexible pattern search when needed
```

### CODE EDITING & MODIFICATION

**SERENA for Surgical Precision:**
```
- replace_symbol_body: Replace entire functions/classes
- insert_after_symbol / insert_before_symbol: Precise code insertion
- Preferred for: Symbol-level changes, language-aware edits
```

**CURSOR for Bulk Operations:**
```
- search_replace: Simple find/replace operations
- MultiEdit: Multiple changes in one file
- Preferred for: Text-based changes, bulk modifications
```

### KNOWLEDGE MANAGEMENT

**SERENA Memory System:**
```
- write_memory: Store project insights for future sessions
- read_memory: Recall previous learnings
- list_memories: Check available knowledge
```

---

## INTELLIGENT WORKFLOWS

### WORKFLOW 1: New Codebase Understanding
```
1. codebase_search("project architecture") // Fast high-level grasp
2. list_dir(".") // Structure overview  
3. codebase_search("main entry points") // Find starting points
4. mcp_serena_get_symbols_overview(key_files) // Symbol-level understanding
5. mcp_serena_write_memory("project-overview", insights) // Persist learning
```

### WORKFLOW 2: Feature Implementation
```
1. codebase_search("similar feature implementation") // Learn patterns
2. mcp_serena_find_symbol(target_class/function) // Locate exact symbols
3. mcp_serena_find_referencing_symbols() // Understand dependencies  
4. mcp_serena_replace_symbol_body() OR search_replace() // Make changes
5. read_lints() // Validate changes
```

### WORKFLOW 3: Bug Investigation
```
1. grep_search(error_message) // Quick error location
2. mcp_serena_find_symbol(problematic_function) // Get symbol details
3. mcp_serena_find_referencing_symbols() // Trace call sites
4. codebase_search("similar bug patterns") // Learn from codebase
5. Precise editing with Serena tools
```

---

## EFFICIENCY RULES

### DO:
- **Parallel Execution:** Run multiple read-only tools simultaneously
- **Strategic Reading:** Use read_file with offset/limit for large files
- **Memory First:** Check mcp_serena_read_memory() before re-discovery
- **Symbol-First:** Prefer symbol-based operations over line-based when possible
- **Context Validation:** Confirm understanding before making changes

### DON'T:
- Read entire large files without exploring first
- Use codebase_search for exact symbol names (use mcp_serena_find_symbol)
- Use Serena for simple text replacements (use Cursor search_replace)
- Ignore Serena memory system for knowledge persistence
- Make assumptions without validation

---

## DECISION LOGIC

### **When to use CURSOR:**
- Initial codebase exploration
- Fast text/pattern searching  
- Bulk text operations
- File management operations
- Quick validation checks

### **When to use SERENA MCP:**
- Symbol-level understanding needed
- Precise code modifications
- Cross-reference analysis
- Language-specific operations
- Knowledge persistence required

### **When to use BOTH:**
- Complex feature implementation
- Comprehensive refactoring
- Bug investigation across multiple files
- Learning new codebase patterns

---

## QUALITY GATES

### **Before Any Code Changes:**
- [ ] Full context understanding achieved
- [ ] Dependencies and references mapped
- [ ] Impact scope assessed
- [ ] Appropriate tool selected for precision level needed

### **After Code Changes:**
- [ ] read_lints() validation completed
- [ ] Changes tested if possible
- [ ] Knowledge updated in Serena memory
- [ ] Documentation updated if needed

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

| Task Type | Primary Tool | Secondary Tool | Key Principle |
|-----------|--------------|----------------|---------------|
| **Explore Unknown Code** | Cursor codebase_search | Serena symbols | Fast → Precise |
| **Find Specific Symbol** | Serena find_symbol | Cursor grep | Precision first |
| **Understand Dependencies** | Serena find_referencing | Cursor codebase_search | Symbol-level accuracy |
| **Bulk Text Changes** | Cursor MultiEdit | Serena regex | Efficiency for scale |
| **Surgical Code Edits** | Serena symbol tools | - | Language-aware precision |
| **Knowledge Management** | Serena memory | - | Persistence across sessions |

**REMEMBER:** Choose the RIGHT tool for the RIGHT precision level for the RIGHT task. Fast exploration → Precise understanding → Accurate modification.
