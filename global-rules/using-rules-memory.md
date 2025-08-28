---
alwaysApply: true
---

# PROJECT MEMORY & CACHE MANAGEMENT RULES

## Core Philosophy: Complete LLM Understanding

**MANDATORY TRIGGERS:**
- New project: "hiểu dự án này" or "understand this project"
- Memory update: "cập nhật memory dự án" or "update project memory"
- Cache issues: Response time > 10s, errors > 5%, cache age > 30 days
- Major changes: >20% files modified

**GOAL:** Create comprehensive memory system for complete LLM project understanding with optimized cache performance.

---

## QUICK START WORKFLOW

### 1. Project Initialization
```python
# ALWAYS start here
mcp_serena_activate_project(project_path)
mcp_serena_check_onboarding_performed()

# Check and reset cache if needed
if check_cache_health().needs_reset:
    reset_llm_cache()
    warm_cache_after_reset()

# Create comprehensive memories
create_complete_project_context()
```

### 2. Memory Update Process
```python
def update_project_memory_and_cache():
    # 1. Health check & cache reset if needed
    cache_health = check_cache_health()
    if cache_health.needs_reset:
        reset_llm_cache()
        warm_cache_after_reset()
    
    # 2. Analyze current state
    current_state = analyze_complete_project()
    
    # 3. Update all memories
    update_all_memories(current_state)
    
    # 4. Validate and optimize
    validate_memory_consistency()
    optimize_for_llm_consumption()
    
    return "Memory and cache updated successfully"
```

---

## MEMORY STRUCTURE FOR COMPLETE LLM UNDERSTANDING

### Essential Memories (MUST CREATE)
1. **project-overview**: Purpose, architecture, current status
2. **technical-stack**: Languages, frameworks, dependencies
3. **architecture-patterns**: Design patterns, data flow, integrations
4. **llm-understanding-guide**: Complete context for LLM comprehension
5. **quick-reference**: Instant access to key information
6. **business-context**: Core workflows, rules, data models
7. **development-workflows**: Patterns, conventions, procedures

### Enhanced Project Overview Template
```markdown
# Project: [Name] - Complete LLM Context

## Project Identity
- **Purpose**: [What problem solved?]
- **Domain**: [Business/technical area]
- **Scale**: [Small/Medium/Large]
- **Maturity**: [Prototype/Development/Production]

## Architecture Overview
- **Pattern**: [MVC, Microservices, etc.]
- **Data Flow**: [How data moves]
- **Integrations**: [External services, APIs]
- **Technology Stack**: [Languages, frameworks]

## Code Organization
- **Structure**: [How code is organized]
- **Conventions**: [Naming, patterns]
- **Entry Points**: [Main files]
- **Configuration**: [Settings, environment]

## Business Logic
- **Core Workflows**: [Main processes]
- **Data Models**: [Key entities]
- **Business Rules**: [Constraints, validations]
- **User Journeys**: [How users interact]

## Development Context
- **Setup**: [How to install/run]
- **Testing**: [Test strategy]
- **Deployment**: [How deployed]
- **Troubleshooting**: [Common issues]
```

---

## CACHE MANAGEMENT SYSTEM

### Cache Types
- **Serena Cache** (.serena/cache/): Symbol analysis, code structure
- **LLM Memory** (.serena/memories/): Project understanding, patterns

### Health Monitoring
```python
def check_cache_health():
    return CacheStatus(
        response_time=measure_llm_response(),
        cache_age=get_cache_age_days(),
        error_rate=get_error_rate(),
        needs_reset=(response_time > 10 or age > 30 or errors > 0.05)
    )
```

### Reset Triggers
- Performance: Response time > 10 seconds
- Age: Cache older than 30 days  
- Errors: Error rate > 5%
- Changes: >20% files modified
- Manual: User requests reset

### Cache Optimization
```python
def warm_cache_after_reset():
    # Pre-load critical files
    critical_files = ["README.md", "requirements.txt", "main.py", "settings.py"]
    for file in critical_files:
        if exists(file): mcp_serena_read_file(file)
    
    # Pre-generate common queries
    common_queries = ["structure", "entry points", "config", "models", "APIs"]
    for query in common_queries:
        mcp_serena_search_for_pattern(query)
```

---

## IMPLEMENTATION COMMANDS

### New Project Setup
```python
# User: "hiểu dự án này"
mcp_serena_activate_project(project_path)
reset_llm_cache()
create_comprehensive_memories()
```

### Memory & Cache Update  
```python
# User: "cập nhật memory dự án"
update_project_memory_and_cache()
```

### Performance Issues
```python
# When LLM slow/inaccurate
reset_llm_cache()
warm_cache_after_reset()
validate_cache_consistency()
```

### Complete Context Loading
```python
def load_complete_context():
    essential_memories = [
        "project-overview", "technical-stack", "architecture-patterns",
        "llm-understanding-guide", "business-context", "quick-reference"
    ]
    return {mem: mcp_serena_read_memory(mem) for mem in essential_memories}
```

---

## QUALITY ASSURANCE

### Memory Validation Checklist
- [ ] **Accuracy**: All paths and references correct
- [ ] **Completeness**: Key components documented
- [ ] **Consistency**: Cross-memory coherence
- [ ] **Relevance**: Important information only
- [ ] **Clarity**: Well-organized and understandable
- [ ] **Actionability**: Helps future development

### Success Criteria
- **Project Understanding**: LLM knows purpose, architecture, patterns
- **Code Navigation**: LLM can find and understand any component  
- **Business Logic**: LLM understands workflows and rules
- **Development Help**: LLM can assist with coding, debugging, deployment
- **Performance**: Response time < 10s, error rate < 5%

---

## ADVANCED STRATEGIES

### Comprehensive Memory Creation
```python
def create_comprehensive_llm_context():
    memories = {
        # Core understanding
        "project-overview": create_enhanced_overview(),
        "technical-stack": analyze_tech_stack(),
        "architecture-patterns": document_architecture(),
        
        # LLM-specific guides
        "llm-understanding-guide": create_comprehension_guide(),
        "quick-reference": create_instant_reference(),
        "troubleshooting-guide": create_problem_reference(),
        
        # Business & operational
        "business-context": extract_business_logic(),
        "development-workflows": analyze_dev_patterns(),
        "deployment-procedures": document_deployment()
    }
    
    for name, content in memories.items():
        mcp_serena_write_memory(name, content)
```

### Cache Performance Optimization
```python
def optimize_memory_for_llm():
    # Structure hierarchically
    hierarchy = {
        'essential': ['project-overview', 'quick-reference'],
        'architectural': ['technical-stack', 'architecture-patterns'], 
        'operational': ['development-workflows', 'troubleshooting-guide']
    }
    
    # Create cross-references and optimize for common queries
    create_memory_cross_references(hierarchy)
    create_query_optimization_cache()
```

---

## MAINTENANCE

### Daily Health Check
```python
def daily_maintenance():
    health = check_cache_health()
    if health.needs_reset:
        reset_llm_cache()
        warm_cache_after_reset()
    else:
        optimize_existing_cache()
```

### Manual Operations
```python
# Force reset: reset_llm_cache()
# Selective update: selective_cache_update(changed_files)  
# Validation: validate_cache_consistency()
# Optimization: optimize_memory_for_llm_consumption()
```

**REMEMBER**: The goal is complete LLM understanding - after reading memories, any LLM should fully comprehend the project's purpose, architecture, business logic, and be able to assist with development tasks effectively.
