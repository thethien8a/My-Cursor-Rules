## PROJECT MEMORY MANAGEMENT RULES

### Core Philosophy: Intelligent Project Context Capture

**MANDATORY TRIGGER CONDITIONS:**
- User enters a new project workspace
- User says "cập nhật memory dự án" or "update project memory"
- User asks "hiểu dự án này" or "understand this project"
- First time working with a project after activation

**GOAL:** Create comprehensive, intelligent memory system that automatically understands and updates project context.

---

## PROJECT INITIALIZATION WORKFLOW

### Phase 1: Project Activation & Discovery (MANDATORY)

#### Step 1: Project Activation
```python
# ALWAYS start with project activation
mcp_serena_activate_project(project_name_or_path)
mcp_serena_check_onboarding_performed()
```

#### Step 2: Structure Discovery
```python
# Get comprehensive project overview
mcp_serena_get_symbols_overview(relative_path="{file_path}")
mcp_serena_list_dir(relative_path=".", recursive=True)
```

#### Step 3: Technology Stack Identification
```python
# Identify key technologies and frameworks
mcp_serena_search_for_pattern("requirements\\.txt|package\\.json|pom\\.xml|build\\.gradle|Cargo\\.toml|go\\.mod")
mcp_serena_search_for_pattern("Dockerfile|docker-compose|dockerfile")
mcp_serena_search_for_pattern("\\.env|config\\.|settings\\.|application\\.properties")
```

#### Step 4: Architecture Analysis
```python
# Understand project structure and patterns
mcp_serena_find_symbol("main|app|index|startup")  # functions
mcp_serena_find_symbol("class|interface|struct")  # classes/interfaces
mcp_serena_search_for_pattern("import|from|require|using")
```

### Phase 2: Deep Context Analysis

#### Step 5: Key Files Analysis
```python
# Analyze critical project files
critical_files = [
    "README.md", "README.txt", "CHANGELOG.md", "LICENSE",
    "requirements.txt", "package.json", "pom.xml", "build.gradle",
    "Dockerfile", "docker-compose.yml", ".env.example",
    "config/", "src/", "app/", "main/"
]

for file_pattern in critical_files:
    mcp_serena_search_for_pattern(file_pattern)
```

#### Step 6: Code Patterns Discovery
```python
# Find architectural patterns and conventions
mcp_serena_search_for_pattern("def main|if __name__|public static void main|func main")
mcp_serena_search_for_pattern("class.*Controller|class.*Service|class.*Repository|class.*Model")
mcp_serena_search_for_pattern("router\\.|app\\.|express\\.|flask\\.|django\\.|spring\\.|fastapi\\.")
```

#### Step 7: Database & Configuration Analysis
```python
# Database and configuration patterns
mcp_serena_search_for_pattern("database|db|sql|mongo|redis|postgres|mysql")
mcp_serena_search_for_pattern("config|settings|environment|env|properties")
mcp_serena_search_for_pattern("migration|schema|model|entity")
```

### Phase 3: Memory Creation & Organization

#### Step 8: Create Core Memory Files
```python
# Create comprehensive project memory
mcp_serena_write_memory("project-overview", comprehensive_project_summary)
mcp_serena_write_memory("technical-stack", technology_analysis)
mcp_serena_write_memory("architecture-patterns", architectural_insights)
mcp_serena_write_memory("development-conventions", coding_patterns)
mcp_serena_write_memory("project-structure", file_organization)
```

#### Step 9: Create Specialized Memory Files
```python
# Create specialized context memories
mcp_serena_write_memory("api-endpoints", api_analysis)
mcp_serena_write_memory("database-schema", database_structure)
mcp_serena_write_memory("deployment-config", deployment_info)
mcp_serena_write_memory("development-workflow", workflow_patterns)
```

---

## PROJECT MEMORY UPDATE WORKFLOW

### Trigger: "cập nhật memory dự án"

#### Step 1: Current State Assessment
```python
# Read existing memories to understand current context
mcp_serena_read_memory("project-overview")
mcp_serena_read_memory("technical-stack")
mcp_serena_read_memory("architecture-patterns")
```

#### Step 2: Change Detection
```python
# Detect what has changed since last update
mcp_serena_get_symbols_overview(relative_path=".")
mcp_serena_search_for_pattern("TODO|FIXME|HACK|NOTE|CHANGED|UPDATED")
mcp_serena_search_for_pattern("def.*new|class.*new|function.*new")
```

#### Step 3: Incremental Analysis
```python
# Focus on new or modified components
mcp_serena_find_symbol("recently_added|new_feature|updated")
mcp_serena_search_for_pattern("recently|newly|updated|modified|changed")
```

#### Step 4: Memory Update Strategy
```python
# Update memories with new information
mcp_serena_write_memory("project-overview", updated_summary)
mcp_serena_write_memory("recent-changes", change_log)
mcp_serena_write_memory("current-state", current_analysis)
```

---

## MEMORY TEMPLATES & STRUCTURE

### Project Overview Template
```markdown
# Project: [Project Name]

## Project Purpose
- **Primary Goal**: [Main objective]
- **Target Users**: [Who uses this]
- **Key Features**: [Core functionality]

## Architecture Overview
- **Technology Stack**: [Languages, frameworks, databases]
- **Architecture Pattern**: [MVC, Microservices, etc.]
- **Deployment**: [How it's deployed]

## Project Structure
- **Root Directories**: [Key folders and their purposes]
- **Entry Points**: [Main files that start the application]
- **Configuration**: [Where settings are stored]

## Development Setup
- **Dependencies**: [How to install requirements]
- **Environment**: [Required environment variables]
- **Build Process**: [How to build/run the project]

## Key Components
- **Frontend**: [UI framework and structure]
- **Backend**: [Server-side components]
- **Database**: [Data storage and models]
- **API**: [External interfaces]

## Current Status
- **Development Phase**: [Current stage]
- **Known Issues**: [Any problems or limitations]
- **Next Steps**: [Immediate priorities]
```

### Technical Stack Template
```markdown
# Technical Stack Analysis

## Core Technologies
- **Language**: [Primary programming language]
- **Framework**: [Main framework used]
- **Database**: [Data storage solution]
- **Frontend**: [UI technologies]

## Dependencies
- **Production Dependencies**: [Key packages]
- **Development Dependencies**: [Dev tools]
- **Version Constraints**: [Important versions]

## Build Tools
- **Package Manager**: [npm, pip, maven, etc.]
- **Build System**: [How code is compiled/bundled]
- **Testing Framework**: [Testing tools used]

## Deployment
- **Containerization**: [Docker, etc.]
- **CI/CD**: [Automation tools]
- **Hosting**: [Where it's deployed]
```

### Architecture Patterns Template
```markdown
# Architecture Patterns

## Design Patterns
- **MVC/MVT**: [Model-View-Controller usage]
- **Repository Pattern**: [Data access patterns]
- **Service Layer**: [Business logic organization]
- **Dependency Injection**: [How dependencies are managed]

## File Organization
- **Module Structure**: [How code is organized]
- **Naming Conventions**: [File/class naming rules]
- **Import Patterns**: [How modules are imported]

## Data Flow
- **Request Processing**: [How requests are handled]
- **Database Operations**: [Data access patterns]
- **Error Handling**: [Exception management]

## Testing Strategy
- **Unit Tests**: [Component testing approach]
- **Integration Tests**: [System testing]
- **Test Organization**: [How tests are structured]
```

---

## INTELLIGENT MEMORY UPDATE RULES

### Rule #1: Context-Aware Updates
```
WHEN UPDATING MEMORY:
- Focus on structural changes (new files, deleted files, moved components)
- Identify new patterns or conventions
- Update technology stack if new dependencies added
- Track architectural evolution
- Note breaking changes or migrations

DON'T UPDATE:
- Temporary files or build artifacts
- Minor code changes without architectural impact
- Personal development notes
- Debugging information
```

### Rule #2: Memory Hierarchy
```
PRIORITY ORDER FOR MEMORY UPDATES:
1. project-overview (always update first)
2. technical-stack (if dependencies changed)
3. architecture-patterns (if structure evolved)
4. recent-changes (for incremental updates)
5. current-state (for immediate context)
6. specialized memories (api-endpoints, database-schema, etc.)
```

### Rule #3: Change Detection Strategy
```
DETECT CHANGES BY:
- Comparing current symbols with previous memory
- Looking for new file patterns
- Identifying modified entry points
- Checking for new dependencies
- Analyzing updated configuration files
- Reviewing recent commit patterns (if available)
```

### Rule #4: Memory Validation
```
BEFORE WRITING MEMORY:
- Verify information is accurate and current
- Ensure consistency across related memories
- Check that patterns are actually used (not just declared)
- Validate that file paths and references are correct
- Confirm that architectural decisions are reflected in code
```

---

## AUTOMATED MEMORY UPDATE WORKFLOW

### Trigger: "cập nhật memory dự án"

#### Automated Process:
```python
def update_project_memory():
    # 1. Load existing context
    existing_memories = load_all_memories()
    
    # 2. Analyze current state
    current_structure = analyze_project_structure()
    current_patterns = identify_architectural_patterns()
    current_technologies = detect_technology_stack()
    
    # 3. Compare with previous state
    changes = detect_significant_changes(existing_memories, current_structure)
    
    # 4. Update memories intelligently
    if changes.detected:
        update_project_overview(changes)
        update_technical_stack(changes)
        update_architecture_patterns(changes)
        create_recent_changes_memory(changes)
    
    # 5. Validate updates
    validate_memory_consistency()
    
    return "Memory updated successfully with X changes detected"
```

---

## MEMORY QUALITY ASSURANCE

### Validation Checklist
- [ ] **Accuracy**: All file paths and references are correct
- [ ] **Completeness**: Key components and patterns are documented
- [ ] **Consistency**: Information across memories is coherent
- [ ] **Relevance**: Only important, lasting information is stored
- [ ] **Clarity**: Information is well-organized and understandable
- [ ] **Actionability**: Memory helps with future development tasks

### Memory Health Metrics
```
MEMORY QUALITY INDICATORS:
- Comprehensive project overview exists
- Technical stack is accurately documented
- Architecture patterns are clearly described
- Recent changes are tracked
- File structure is well-mapped
- Key components are identified
- Development workflow is documented
```

---

## SUCCESS CRITERIA

### For Project Initialization:
- [ ] Project is activated and accessible
- [ ] Core memories are created (project-overview, technical-stack, architecture-patterns)
- [ ] Key files and patterns are identified
- [ ] Technology stack is accurately documented
- [ ] Development workflow is understood
- [ ] Entry points and main components are mapped

### For Memory Updates:
- [ ] Changes are detected and documented
- [ ] Memories are updated with new information
- [ ] Consistency is maintained across memories
- [ ] Recent changes are tracked
- [ ] Current state is accurately reflected
- [ ] No outdated information remains

---

## IMPLEMENTATION COMMANDS

### For New Project:
```python
# User says: "hiểu dự án này" or enters new project
mcp_serena_activate_project("{project path}")
mcp_serena_check_onboarding_performed()
# Follow Phase 1-3 workflow above
```

### For Memory Update:
```python
# User says: "cập nhật memory dự án"
# Follow Project Memory Update Workflow above
```

### For Quick Context Check:
```python
# User asks about project understanding
mcp_serena_read_memory("project-overview")
mcp_serena_read_memory("current-state")
# Provide summary based on memories
```

---