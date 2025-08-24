# MANDATORY RULES FOR READING FILES

## EXTREMELY LARGE FILES — TOP-LEVEL OVERRIDE
- **Definition**: Consider a file extremely large if >100K lines or >10MB, or when size is unknown but suspected to be huge.
- **Hard rules**:
  - **NEVER** full-read the file. Avoid unbounded `read_file()` calls.
  - **NO TERMINAL/CLI** for size checks. Use Serena-only strategies.
  - Cap total reading to ≤2,000 lines per turn from such files.
- **Minimal playbook (Serena-first)**:
  1) **Overview-first (code files)**: `mcp_serena_get_symbols_overview(relative_path=path)`
  2) **Head sample**: `mcp_serena_read_file(relative_path=path, start_line=0, end_line=200, max_answer_chars=120000)`
  3) **Targeted retrieval**:
     - Search: `mcp_serena_search_for_pattern(substring_pattern=query, context_lines_before=20, context_lines_after=20, relative_path=path)`
     - Then bounded read around hits using `start_line`/`end_line` windows only
  4) **User-guided chunk**: Ask for keywords/sections, then read only those bounded regions
- **Fallback**:
  - If Serena returns no content, use Cursor `read_file()` on a small, bounded range only (e.g., first 200 lines). Do not attempt full reads.
- **Stop criteria**: As soon as you obtain the relevant snippet, stop reading, summarize, and propose the next minimal read if needed.

```python
# EXTREME FILE SAFE READ (no terminal)
overview = mcp_serena_get_symbols_overview(relative_path=path)
head = mcp_serena_read_file(relative_path=path, start_line=0, end_line=200, max_answer_chars=120000)
hits = mcp_serena_search_for_pattern(substring_pattern=query, context_lines_before=20, context_lines_after=20, relative_path=path)
if hits:
    # Read a narrow window around the first hit (example)
    start = max(0, hits[0].start_line - 100)
    end = hits[0].end_line + 100
    focus = mcp_serena_read_file(relative_path=path, start_line=start, end_line=end, max_answer_chars=120000)
```

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

### Handling Large Files (SMART STRATEGY):

#### Size-Based Reading Strategy:
- **Small** (<1MB): Read normally with Serena
- **Medium** (1-10MB): Use `max_answer_chars=200000` 
- **Large** (10-100MB): Intelligent sampling + targeted reading
- **Mega** (>100MB): **NEVER read entirely** - Use smart exploration only

#### Mega File Strategy (>100MB or >1M lines):
1. **File Analysis First**: Use `mcp_serena_get_symbols_overview` to understand structure
2. **Intelligent Sampling**: Read first 100 + middle 100 + last 100 lines only
3. **Targeted Search**: Use `mcp_serena_search_for_pattern` for specific needs
4. **User-Guided Chunks**: Ask user what they need, read specific sections only
5. **NEVER**: Attempt full file reading - always explain size risk to user

#### Progressive Reading Template:
```python
# STEP 1: Check file size first (MANDATORY for large files)
file_info = get_file_info(filename)  # Use OS tools if available

# STEP 2: Size-based strategy
if file_info.size > 100_000_000:  # >100MB
    # MEGA FILE - Smart exploration only
    explain_size_risk_to_user()
    use_intelligent_sampling()
    use_targeted_search_only()
elif file_info.size > 10_000_000:  # >10MB 
    # LARGE FILE - Sampling + guided reading
    use_intelligent_sampling()
    ask_user_for_specific_needs()
else:
    # Normal reading with appropriate limits
    mcp_serena_read_file(relative_path=filename, max_answer_chars=200000)
```

### Example (FOLLOW THIS EXACTLY):
```python
# STEP 1: Ensure project is active
try:
    mcp_serena_check_onboarding_performed()
except:
    mcp_serena_activate_project("project_name")
    mcp_serena_check_onboarding_performed()

# STEP 2: Smart file size handling (NEW)
try:
    # Try to get file size/line count first
    file_stats = run_terminal_cmd(f"wc -l {filename}")  # Or equivalent
    line_count = int(file_stats.split()[0]) if file_stats else 0
    
    if line_count > 1_000_000:  # >1M lines = MEGA FILE
        print(f"MEGA FILE DETECTED: {line_count:,} lines")
        print("Using smart exploration instead of full read")
        # Use intelligent sampling + targeted search only
        sampling_result = intelligent_file_sampling(filename)
        return sampling_result
        
    elif line_count > 100_000:  # >100K lines = LARGE FILE  
        print(f"LARGE FILE: {line_count:,} lines - using sampling strategy")
        result = mcp_serena_read_file(relative_path=filename, max_answer_chars=200000)
        
    else:
        # Normal size file
        result = mcp_serena_read_file(relative_path=filename)
        
except:
    # Fallback to normal Serena read if size detection fails
    result = mcp_serena_read_file(relative_path=filename)

# STEP 3: Only use Cursor if Serena failed or returned empty
if not result or result.empty:
    read_file(target_file=filename)
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
# STEP 1: Smart size detection (MANDATORY for large files)
def smart_file_read(filename):
    try:
        # Quick size check
        file_stats = run_terminal_cmd(f"wc -l {filename}")
        line_count = int(file_stats.split()[0]) if file_stats else 0
        
        if line_count > 1_000_000:  # MEGA FILE
            return handle_mega_file(filename, line_count)
        elif line_count > 100_000:  # LARGE FILE
            return handle_large_file(filename, line_count)
        else:
            return mcp_serena_read_file(relative_path=filename)
    except:
        return mcp_serena_read_file(relative_path=filename)

def handle_mega_file(filename, line_count):
    print(f"MEGA FILE: {line_count:,} lines - Smart exploration only")
    # 1. Symbol overview first
    overview = mcp_serena_get_symbols_overview(relative_path=filename)
    # 2. Intelligent sampling: first + middle + last
    sample = read_file_sample(filename, sample_size=300)
    # 3. Ask user for specific needs
    print("What specific content are you looking for in this mega file?")
    return {"overview": overview, "sample": sample}

def handle_large_file(filename, line_count):
    print(f"LARGE FILE: {line_count:,} lines - Using optimized reading")
    return mcp_serena_read_file(relative_path=filename, max_answer_chars=200000)
```

### Creating Files:
```python
# Preferred method
edit_file(target_file="new_file.py", instructions="Create file", code_edit="content")

# Fallback method
mcp_serena_create_text_file(relative_path="new_file.py", content="content")
```

## ERROR HANDLING - SMART STRATEGY

### Size-Based Error Handling:
- **Normal files**: If Serena fails → Use Cursor read_file as fallback
- **Large files (>100K lines)**: If Serena fails → Use intelligent sampling + ask user
- **Mega files (>1M lines)**: **NEVER attempt full read** → Always use smart exploration
- **Unknown size**: Try Serena with max_answer_chars=200000 → If fails, detect size and retry

### Mega File Protection (CRITICAL):
```python
def safe_mega_file_handling(filename, line_count):
    if line_count > 1_000_000:
        print(f"PROTECTION: File has {line_count:,} lines")
        print("Full reading blocked to prevent context overflow")
        print("Using smart exploration instead")
        
        # Safe alternatives:
        # 1. Symbol overview only
        # 2. Targeted search based on user query
        # 3. Intelligent sampling (300 lines max)
        # 4. User-guided chunk reading
        
        return use_smart_exploration_only(filename)
    

def context_overflow_prevention():
    # NEVER allow these dangerous operations on mega files:
    # - mcp_serena_read_file() without size check
    # - read_file() on files >1M lines
    # - Full context loading for mega files
    # - Always use sampling + targeted search
    pass
```

### Fallback Priority:
1. **First**: Size detection + appropriate strategy
2. **Second**: Serena with limits based on detected size
3. **Third**: Intelligent sampling if size too large
4. **Last**: Explain to user and ask for guidance
5. **NEVER**: Attempt dangerous full read of mega files

## SUMMARY FOR LLM - SMART FILE READING

**EVERY TIME YOU READ A FILE:**

### MANDATORY WORKFLOW:
1. **Size Detection FIRST**: Check file size/line count before reading
2. **Smart Strategy Selection**:
   - Normal (<100K lines): Serena → Cursor fallback
   - Large (100K-1M lines): Serena with limits → Sampling
   - **Mega (>1M lines): SMART EXPLORATION ONLY - NO FULL READ**
3. **Context Protection**: Never overflow context with mega files

### SIZE-BASED RULES:
- **<100K lines**: `mcp_serena_read_file()` → `read_file()` fallback
- **100K-1M lines**: `mcp_serena_read_file(max_answer_chars=200000)` → sampling
- **>1M lines**: Symbol overview + intelligent sampling + targeted search ONLY

### MEGA FILE PROTECTION:
- **NEVER** attempt full read of files >1M lines
- **ALWAYS** use smart exploration: overview + sampling + targeted search
- **ASK USER** what specific content they need from mega files
- **EXPLAIN** size risks and protection measures to user

### SAFETY PRINCIPLE:
**Better to ask user for guidance than to overflow context with mega file**
