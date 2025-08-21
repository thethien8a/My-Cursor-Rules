# MANDATORY RULES FOR READING FILS

## CRITICAL FILE READING RULE - NO EXCEPTIONS
**ALWAYS USE SERENA FIRST FOR ALL FILE READING**

### SIMPLE RULE: 
**Try mcp_serena_read_file FIRST. Only use read_file if Serena returns no content.**

### Step-by-Step (MANDATORY):
1. **FIRST**: Try `mcp_serena_read_file(relative_path="filename")`
2. **CHECK**: If Serena returns content → DONE, do not use Cursor read_file
3. **FALLBACK**: If Serena returns empty/no content → Then use `read_file(target_file="filename")`

### Project Initialization Required:
- Before using Serena tools, check if project is active
- If no project active, activate with `mcp_serena_activate_project("project_name")`
- Then check onboarding with `mcp_serena_check_onboarding_performed()`

### Handling Large Files:
- If Serena fails due to file size, use `max_answer_chars` parameter
- For very large files, read in chunks using `start_line` and `end_line`
- Alternative: Use `mcp_serena_search_for_pattern` to find specific content

### Example (FOLLOW THIS EXACTLY):
```python
# STEP 1: Ensure project is active
try:
    mcp_serena_check_onboarding_performed()
except:
    mcp_serena_activate_project("project_name")
    mcp_serena_check_onboarding_performed()

# STEP 2: Try Serena first
result = mcp_serena_read_file(relative_path="file.py")

# STEP 3: Only use Cursor if Serena failed or returned empty
if not result or result.empty:
    read_file(target_file="file.py")

# For large files, try with max_answer_chars
if "too long" in str(result):
    mcp_serena_read_file(relative_path="file.py", max_answer_chars=500000)
```

## File Creation/Editing Priority  
**RULE #2: Always use Cursor tools first for file operations, fallback to Serena**
- **Primary**: Use Cursor's `edit_file` and `create_text_file` for all file modifications
- **Fallback**: If Cursor tools fail (permission, syntax error, etc.), then use Serena MCP tools
- **Why**: Cursor tools are more reliable for direct file manipulation in the editor

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

## QUICK REFERENCE - COPY THIS EXACTLY

### Reading Files (USE THIS TEMPLATE):
```python
# STEP 1: ALWAYS try Serena first (MANDATORY)
result = mcp_serena_read_file(relative_path="filename.extension")

# STEP 2: Only use Cursor if Serena failed or returned empty
if not result or len(result) == 0:
    read_file(target_file="filename.extension")

# For large files, try with increased limit
if "too long" in str(result):
    mcp_serena_read_file(relative_path="filename.extension", max_answer_chars=500000)
```

### Creating Files:
```python
# Preferred method
edit_file(target_file="new_file.py", instructions="Create file", code_edit="content")

# Fallback method
mcp_serena_create_text_file(relative_path="new_file.py", content="content")
```

## ERROR HANDLING - SIMPLIFIED
- **If Serena returns content**: DONE, do not use Cursor read_file
- **If Serena fails or returns empty**: Use Cursor read_file as fallback
- **If file too large**: Try Serena with max_answer_chars=500000
- **If both fail**: Report error to user
- **NEVER skip Serena**: Always try mcp_serena_read_file first, no exceptions

## SUMMARY FOR LLM
**EVERY TIME YOU READ A FILE:**
1. `mcp_serena_read_file(relative_path="filename")` ← ALWAYS TRY FIRST
2. `read_file(target_file="filename")` ← ONLY if Serena failed/empty
3. Priority: Serena first, Cursor only as fallback when needed
