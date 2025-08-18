# 🎯 MANDATORY RULES FOR CURSOR AI EDITOR WORKFLOW

## 📖 File Reading Priority
**RULE #1: Check Serena project initialization before reading**
- **Initialization check (MANDATORY)**: Verify Serena project is initialized.
  - Preferred: `mcp_serena_check_onboarding_performed()`; if it errors or reports no active project, treat as not initialized.
- **If NOT initialized**: Use Cursor `read_file` only.
- **If initialized**: Use BOTH in order: first `mcp_serena_read_file`, then Cursor `read_file`.
- **Why**: Ensures Serena’s semantic context is used when available; maintains IDE visibility and consistent behavior.

- **Example**:
```python
# Step 0: Check Serena project initialization
init_ok = mcp_serena_check_onboarding_performed()

if not init_ok:
    # Project NOT initialized → use Cursor only
    read_file(target_file="file.py")
else:
    # Project initialized → use both Serena + Cursor
    mcp_serena_read_file(relative_path="file.py")
    read_file(target_file="file.py")
```

## ✏️ File Creation/Editing Priority  
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

## 🔄 Workflow Decision Tree

### For File Reading:
```
0. Check Serena project initialization
   ↓
1. If NOT initialized → use Cursor read_file() and stop
   ↓
2. If initialized → run mcp_serena_read_file() then read_file() (both)
   ↓
3. If any step fails unexpectedly → Report error to user
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

## ⚡ Quick Reference Commands

### Reading Files:
```python
# Initialization check
mcp_serena_check_onboarding_performed()

# If NOT initialized → Cursor only
read_file(target_file="file.py")

# If initialized → Both Serena then Cursor
mcp_serena_read_file(relative_path="file.py")
read_file(target_file="file.py")
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

## 🎯 Success Criteria
- **File Reading**: Always get file content successfully, even if primary method fails
- **File Operations**: Complete file creation/editing with proper error handling
- **User Experience**: Seamless workflow without manual intervention
- **Error Reporting**: Clear communication when both methods fail

## 📝 Best Practices
1. **Always try the preferred method first**
2. **Handle errors gracefully with fallback**
3. **Report which method was used to user**
4. **Maintain consistency across the project**
5. **Update project memory with successful operations**

## 🚨 Error Handling
- Before reading: If Serena project is not initialized → skip Serena read_file and use Cursor read_file only
- If Serena MCP read_file fails → Immediately try Cursor read_file
- If Cursor edit_file fails → Immediately try Serena MCP tools
- If both fail → Provide clear error message to user
- Always log which method was successful for future reference
