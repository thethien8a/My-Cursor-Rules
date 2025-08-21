# MANDATORY RULES FOR READING FILE

## CRITICAL FILE READING RULE - NO EXCEPTIONS
**ALWAYS USE SERENA FIRST FOR ALL FILE READING**

### SIMPLE RULE: 
**Try mcp_serena_read_file FIRST. Only use read_file if Serena returns no content.**

### Step-by-Step (MANDATORY):
1. **FIRST**: Try `mcp_serena_read_file(relative_path="filename")`
2. **CHECK**: If Serena returns content → DONE, do not use Cursor read_file
3. **FALLBACK**: If Serena returns empty/no content → Then use `read_file(target_file="filename")`

### Why This Rule Exists:
- Serena provides semantic context and project understanding
- Only use Cursor as fallback when Serena fails
- Avoid duplicate reads when Serena works

### Example (FOLLOW THIS EXACTLY):
```python
# STEP 1: ALWAYS try Serena first
result = mcp_serena_read_file(relative_path="file.py")

# STEP 2: Only use Cursor if Serena failed or returned empty
if not result or result.empty:
    read_file(target_file="file.py")

# RULE: Serena first, Cursor only as fallback
```

## File Creation/Editing Priority  
**RULE #2: Always use Cursor tools first for file operations, fallback to Serena**
- **Primary**: Use Cursor's `edit_file` and `create_text_file` for all file modifications
- **Fallback**: If Cursor tools fail (permission, syntax error, etc.), then use Serena MCP tools
- **Why**: Cursor tools are more reliable for direct file manipulation in the editor
- **Example**:
  ```python
  # Try Cursor first
  edit_file(target_file="new_file.py", instructions="Create new file", code_edit="content")
  # If error, use Serena
  mcp_serena_create_text_file(relative_path="new_file.py", content="content")
  ```

## WORKFLOW DECISION TREE

### For File Reading (SIMPLIFIED):
```
EVERY TIME YOU NEED TO READ A FILE:
   ↓
1. FIRST: mcp_serena_read_file(relative_path="filename")
   ↓
2. CHECK: Did Serena return content?
   ↓
3a. YES → DONE (do not use Cursor read_file)
3b. NO → Use read_file(target_file="filename") as fallback
```

### For File Creation/Editing:
```
1. Start with edit_file() or create_text_file() from Cursor
   ↓
2. If SUCCESS → File operation completed
   ↓
3. If ERROR → Switch to Serena MCP tools
   ↓
4. If both fail → Report error to user
```

## QUICK REFERENCE - COPY THIS EXACTLY

### Reading Files (USE THIS TEMPLATE):
```python
# STEP 1: ALWAYS try Serena first (MANDATORY)
result = mcp_serena_read_file(relative_path="filename.extension")

# STEP 2: Only use Cursor if Serena failed or returned empty
if not result or len(result) == 0:
    read_file(target_file="filename.extension")

# RULE: Serena first, Cursor only as fallback when needed
```

### Creating Files:
```python
# Preferred method
edit_file(target_file="new_file.py", instructions="Create file", code_edit="content")

# Fallback method
mcp_serena_create_text_file(relative_path="new_file.py", content="content")
```

### Editing Files:
```python
# Preferred method
edit_file(target_file="existing_file.py", instructions="Update function", code_edit="new code")

# Fallback method
mcp_serena_replace_regex(relative_path="existing_file.py", regex="old_pattern", repl="new_content")
```

## Success Criteria
- **File Reading**: Always get file content successfully, even if primary method fails
- **File Operations**: Complete file creation/editing with proper error handling
- **User Experience**: Seamless workflow without manual intervention
- **Error Reporting**: Clear communication when both methods fail

## Best Practices
1. **Always try the preferred method first**
2. **Handle errors gracefully with fallback**
3. **Report which method was used to user**
4. **Maintain consistency across the project**
5. **Update project memory with successful operations**

## ERROR HANDLING - SIMPLIFIED
- **If Serena returns content**: DONE, do not use Cursor read_file
- **If Serena fails or returns empty**: Use Cursor read_file as fallback
- **If both fail**: Report error to user
- **NEVER skip Serena**: Always try mcp_serena_read_file first, no exceptions

## SUMMARY FOR LLM
**EVERY TIME YOU READ A FILE:**
1. `mcp_serena_read_file(relative_path="filename")` ← ALWAYS TRY FIRST
2. `read_file(target_file="filename")` ← ONLY if Serena failed/empty
3. Priority: Serena first, Cursor only as fallback when needed
