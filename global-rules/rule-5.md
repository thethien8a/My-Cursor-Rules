# Codespace Exploration Rules:

## Core Principle
**Always use the RIGHT TOOL for the RIGHT TASK** - combine Serena's semantic power with Cursor's built-in efficiency.

---

## Decision Matrix: When to Use What

### **Use Serena MCP Tools When:**
- **Semantic Analysis**: Understanding code architecture, patterns, relationships
- **Symbol-Level Operations**: Find/modify specific functions, classes, variables
- **Large Codebase Navigation**: Projects >10k lines, complex dependencies
- **Cross-File Analysis**: Tracing function calls, inheritance, imports
- **Memory-Efficient Ops**: When Cursor is consuming too much RAM

### **Use Cursor Built-in When:**
- **File Operations**: Reading, creating, simple text edits
- **Quick Searches**: Finding literal strings, basic patterns
- **UI Interactions**: Project navigation, terminal commands
- **General Coding**: Writing new code, simple refactoring

---

## Exploration Workflow

### Phase 1: Project Setup & Initial Scan
```
1. Activate Serena: "Activate project [path] using Serena"
2. Get Overview: Use Serena's get_symbols_overview on key files
3. Understand Structure: Ask Serena to analyze project architecture
4. Index (if large): Run serena project index for >50k lines
```

### Phase 2: Deep Exploration  
```
1. Find Entry Points: Use Serena to locate main functions/classes
2. Trace Dependencies: Use find_referencing_symbols for key components
3. Pattern Analysis: Use search_for_pattern for specific implementations
4. Memory Management: Monitor RAM usage, switch tools if needed
```

### Phase 3: Targeted Analysis
```
1. Symbol Deep Dive: Use find_symbol for specific components
2. Context Building: Use Serena's semantic tools to build comprehensive understanding
3. Cross-Reference: Combine Serena findings with Cursor's file browsing
4. Documentation: Use Serena's memory tools to save insights
```

---

## Performance Optimization Rules

### Memory Management
- **Monitor**: Check Cursor RAM usage regularly
- **Switch**: Use Serena for heavy analysis if Cursor >4GB RAM
- **Clean**: Restart tools if memory leaks detected
- **Optimize**: Use selective indexing for massive codebases

### Efficiency Patterns
- **Parallel**: Use Cursor for UI while Serena analyzes in background
- **Cache**: Leverage Serena's symbol cache for repeated queries
- **Scope**: Limit Serena searches to relevant directories
- **Incremental**: Build understanding progressively, don't analyze everything at once

---

## Best Practices

### DO:
- Start with Serena for project overview, then use Cursor for specific tasks
- Use Serena's semantic search before Cursor's text search
- Leverage both tools' strengths simultaneously
- Save important findings using Serena's memory system
- Use project-specific Serena configurations for large codebases

### DON'T:
- Use Cursor's indexing for semantic analysis (use Serena instead)
- Overwhelm Serena with too many simultaneous requests
- Ignore memory usage warnings
- Skip project activation in Serena
- Use text search when semantic search is needed  

---

## Troubleshooting

### High Memory Usage
1. Check which tool is consuming RAM
2. Switch heavy analysis to Serena
3. Restart consuming tool if needed
4. Use selective analysis instead of full codebase scan

### Slow Performance
1. Ensure Serena project is properly indexed
2. Use scoped searches instead of global
3. Check if language servers are running properly
4. Consider breaking large analysis into smaller chunks

### Integration Issues
1. Verify MCP server is running: Check Cursor Settings > MCP
2. Restart MCP server if tools not available
3. Check Serena dashboard at localhost:24282
4. Ensure proper project activation in Serena

---

## Success Metrics
- **Fast Discovery**: Key components identified within minutes
- **Memory Efficient**: Combined tools use <8GB RAM for large projects
- **Comprehensive**: Full codebase understanding achieved systematically
- **Actionable**: Clear next steps identified for any development task
