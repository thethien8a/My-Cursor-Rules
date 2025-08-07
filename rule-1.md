# 🎯 MANDATORY RULES FOR CURSOR AI EDITOR WORKFLOW

## 📖 File Reading Priority
**RULE #1: Always use Serena MCP read_file first, fallback to Cursor**
- **Primary**: Use `mcp_serena_read_file` for all file reading operations
- **Fallback**: If Serena MCP read_file fails (error, timeout, etc.), then use Cursor's `read_file`
- **Why**: Serena MCP provides better file analysis and context understanding
- **Example**: 
  ```python
  # Try Serena first
  mcp_serena_read_file(target_file="file.py")
  # If error, use Cursor
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
1. Start with mcp_serena_read_file()
   ↓
2. If SUCCESS → Use Serena's analysis capabilities
   ↓
3. If ERROR → Switch to read_file() from Cursor
   ↓
4. If both fail → Report error to user
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
# Preferred method
mcp_serena_read_file(relative_path="file.py")

# Fallback method  
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
- If Serena MCP read_file fails → Immediately try Cursor read_file
- If Cursor edit_file fails → Immediately try Serena MCP tools
- If both fail → Provide clear error message to user
- Always log which method was successful for future reference