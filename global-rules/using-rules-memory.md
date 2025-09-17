# RULE 3: PROJECT MEMORY & CACHE MANAGEMENT RULES
_(SUPPORTING PROCESS for ALL PHASES)_

**NOTE:** This rule provides the foundational knowledge system for the project. It is not a sequential phase, but rather an integrated process that supports Rule 1 (Analysis) and Rule 2 (Implementation).

---

## Core Philosophy: Complete LLM Understanding

### MANDATORY TRIGGERS:
- **New project:** "hiểu dự án này" or "understand this project"
- **Memory update:** "cập nhật memory dự án" or "update project memory"
- **Cache issues:** Response time > 10s, errors > 5%, cache age > 30 days
- **Major changes:** >20% files modified

**GOAL:** Create comprehensive memory system for complete LLM project understanding with optimized cache performance.

---

## QUICK START WORKFLOW

### 1. Project Initialization

**ALWAYS start here**
```
mcp_serena_activate_project(project_path)
mcp_serena_check_onboarding_performed()
```

**Check and reset cache if needed**
```
if check_cache_health().needs_reset:
    reset_llm_cache()
    warm_cache_after_reset()
```

**Create comprehensive memories**
```
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

## MEMORY STRUCTURE STORING 

### Optimized Memory Set (MANDATORY - Complete Understanding in 6 Documents)
1.  `project-overview-and-status`: Complete project context, current work tracking, and decision log
2.  `codebase-navigation-map`: Full code structure, patterns, and instant navigation guide
3.  `technical-architecture-and-patterns`: Architecture, data flow, code conventions, and implementation patterns
4.  `development-operations-guide`: Everything needed to develop, test, deploy, and maintain
5.  `llm-quick-reference-index`: Instant lookup for symbols, APIs, common tasks, and gotchas
6.  `project-history-and-evolution`: Project history, milestones, lessons learned, and future evolution plans
*... and more memories if needed*

---

### Detailed Templates for Complete LLM Handoff (stored in `.serena/memories/`)

#### 1. `project-overview-and-status`
**PROJECT IDENTITY**
- **Purpose:** [What problem does this solve?]
- **Domain:** [Business/technical area]
- **Users:** [Who uses this and how]
- **Tech Stack:** [Languages, frameworks, databases, services]

**CURRENT STATE (CRITICAL FOR HANDOFF)**
- **Version/Release:** [Current version in each environment]
- **Active Work:** [What's being worked on RIGHT NOW]
  - Task 1: [Description] - Owner: [Name] - Status: [%] - ETA: [Date]
  - Task 2: [Description] - Owner: [Name] - Status: [%] - ETA: [Date]
- **Recent Changes:** [Last 5 significant changes with dates]
- **Blockers:** [Current issues preventing progress]
- **Next Steps:** [Prioritized list of what comes next]

**DECISION LOG**
- [Date] Decision: [What was decided and why]
- [Date] Decision: [What was decided and why]

#### 2. `codebase-navigation-map`
**INSTANT ORIENTATION**
- **Repository:** [URL/path]
- **Main Entry Point:** [e.g., `src/main.py`, `cmd/server/main.go`]
- **Project Type:** [Web app, API, CLI, Library, etc.]

**DIRECTORY STRUCTURE WITH PURPOSE**
- `/src`
  - `/api` - [REST endpoints, GraphQL resolvers]
  - `/models` - [Data models, DTOs, entities]
  - `/services` - [Business logic, external integrations]
  - `/utils` - [Shared utilities, helpers]
- `/tests` - [Test structure mirrors `src/`]
- `/docs` - [Documentation, ADRs]
- `/scripts` - [Build, deploy, maintenance scripts]

**CODE PATTERNS & CONVENTIONS**
- **Naming:** [CamelCase for classes, snake_case for functions]
- **File Organization:** [One class per file, grouped by feature]
- **Import Style:** [Absolute imports from `src/`]
- **Error Handling:** [Custom exceptions in `errors/`, centralized handling]
- **Testing:** [Unit tests next to code, integration in `tests/`]

**NAVIGATION SHORTCUTS**
- Find authentication: `src/services/auth/`
- Find API endpoints: `src/api/routes/`
- Find database models: `src/models/`
- Find configuration: `src/config/`
- Find tests for X: `tests/X/` or `src/X/test_X.py`

#### 3. `technical-architecture-and-patterns`
**ARCHITECTURE OVERVIEW**
[ASCII diagram or description of main components and data flow]

**CORE COMPONENTS**
- **Component A:** [Purpose, responsibilities, key classes/modules]
- **Component B:** [Purpose, responsibilities, key classes/modules]
- **Component C:** [Purpose, responsibilities, key classes/modules]

**IMPLEMENTATION PATTERNS**
- **Request Flow:** [Client → API Gateway → Service → Database]
- **Authentication:** [JWT/OAuth, where tokens validated]
- **Data Access:** [Repository pattern, ORM usage]
- **Caching:** [Redis for X, in-memory for Y]
- **Error Handling:** [Global error handler, custom exceptions]
- **Logging:** [Structured logging, correlation IDs]

**INTEGRATIONS & DEPENDENCIES**
- **External APIs:** [Service A for X, Service B for Y]
- **Databases:** [PostgreSQL for main data, Redis for cache]
- **Message Queues:** [RabbitMQ for async tasks]
- **Critical Libraries:** [Library versions and why chosen]

**CODE EXAMPLES (PATTERNS TO FOLLOW)**
```python
# Standard service pattern
class UserService:
    def __init__(self, repo: UserRepository):
        self._repo = repo
    
    async def get_user(self, id: str) -> User:
        # Pattern: validate → fetch → transform → return
```

#### 4. `development-operations-guide`
**QUICK START (COPY-PASTE COMMANDS)**
```bash
# Clone and setup
git clone [repo]
cd [project]
python -m venv venv
source venv/bin/activate  # or .\venv\Scripts\activate on Windows
pip install -r requirements.txt
cp .env.example .env
# Edit .env with your values

# Run locally
python src/main.py

# Run tests
pytest
```

**DEVELOPMENT WORKFLOW**
- **Branch Strategy:** [feature/*, bugfix/*, hotfix/*]
- **Commit Convention:** [type(scope): description]
- **PR Process:** [Review required, CI must pass]
- **Local Testing:** [Commands to test before pushing]

**ENVIRONMENTS & DEPLOYMENT**
- **Local:** `http://localhost:8000`
- **Dev:** `https://dev.example.com` (auto-deploy from develop)
- **Staging:** `https://staging.example.com` (manual deploy)
- **Production:** `https://api.example.com` (requires approval)

**COMMON TASKS**
- **Add new endpoint:** [Steps and example]
- **Update database schema:** [Migration commands]
- **Debug production issue:** [Log access, tools]
- **Performance profiling:** [Tools and process]

**TROUBLESHOOTING**
- **Error:** "Module not found" → `pip install -r requirements.txt`
- **Error:** "Database connection failed" → Check `.env` `DATABASE_URL`
- **Error:** "Port already in use" → `lsof -i :8000` and `kill PID`

#### 5. `llm-quick-reference-index`
**INSTANT LOOKUPS**
**Main Classes/Functions:**
- `UserService`: `src/services/user.py` - Handles all user operations
- `AuthMiddleware`: `src/middleware/auth.py` - JWT validation
- `DatabaseConnection`: `src/db/connection.py` - Connection pooling
- `APIRouter`: `src/api/router.py` - Route registration

**Key APIs:**
- `POST /auth/login` - `{"email": "", "password": ""}` → `{"token": ""}`
- `GET /users/:id` - Headers: `{"Authorization": "Bearer token"}` → User object
- `POST /items` - `{"name": "", "price": 0}` → Created item

**Configuration Variables:**
- `DATABASE_URL`: PostgreSQL connection string
- `JWT_SECRET`: Secret for token signing
- `REDIS_URL`: Cache connection
- `LOG_LEVEL`: debug/info/warning/error

**Common Gotchas:**
- Always use async/await for database calls
- JWT tokens expire after 24h
- Rate limiting: 100 req/min per IP
- Database migrations must be reviewed before production

**Symbol Index:**
[Alphabetical list of important symbols and their locations]
- `authenticate()`: `src/services/auth.py:45`
- `User`: `src/models/user.py:12`
- `create_connection()`: `src/db/connection.py:23`

#### 6. `project-history-and-evolution`
**PROJECT HISTORY AND EVOLUTION**

**TIMELINE OF MAJOR MILESTONES**
- [Date]: [Milestone 1] - [Description: What was added/changed, why, impact]
- [Date]: [Milestone 2] - [Description: What was added/changed, why, impact]
- [Ongoing]: [Current phase] - [Key evolutions or pivots]

**LESSONS LEARNED FROM EVOLUTION**
- [Lesson 1]: [What was learned, how it influenced future decisions]
- [Lesson 2]: [What was learned, how it influenced future decisions]

**FUTURE EVOLUTION PLANS**
- [High-level roadmap]: [Anticipated changes based on current trajectory]

---

## CACHE MANAGEMENT SYSTEM

### Cache Types
- **Serena Cache (`.serena/cache/`):** Symbol analysis, code structure
- **LLM Memory (`.serena/memories/`):** Project understanding, patterns

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
- **Performance:** Response time > 10 seconds
- **Age:** Cache older than 30 days
- **Errors:** Error rate > 5%
- **Changes:** >20% files modified
- **Manual:** User requests reset

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
**User:** "hiểu dự án này"
```
mcp_serena_activate_project(project_path)
reset_llm_cache()
create_comprehensive_memories()
```

### Memory & Cache Update
**User:** "cập nhật memory dự án"
```
update_project_memory_and_cache()
```

### Performance Issues
**When LLM slow/inaccurate**
```
reset_llm_cache()
warm_cache_after_reset()
validate_cache_consistency()
```

### Complete Context Loading
```python
def load_complete_context():
    essential_memories = [
        "project-overview-and-status",
        "codebase-navigation-map", 
        "technical-architecture-and-patterns",
        "development-operations-guide",
        "llm-quick-reference-index"
    ]
    return {mem: mcp_serena_read_memory(mem) for mem in essential_memories}
```
---

## QUALITY ASSURANCE

### Memory Validation Checklist
- **Accuracy:** All paths and references correct
- **Completeness:** Key components documented
- **Consistency:** Cross-memory coherence
- **Relevance:** Important information only
- **Clarity:** Well-organized and understandable
- **Actionability:** Helps future development

### Success Criteria
- **Project Understanding:** LLM knows purpose, architecture, patterns
- **Code Navigation:** LLM can find and understand any component
- **Business Logic:** LLM understands workflows and rules
- **Development Help:** LLM can assist with coding, debugging, deployment
- **Performance:** Response time < 10s, error rate < 5%

---

## ADVANCED STRATEGIES

### Comprehensive Memory Creation
```python
def create_comprehensive_llm_context():
    memories = {
        # Core understanding and current state
        "project-overview-and-status": create_complete_project_overview(),
        
        # Code navigation and patterns
        "codebase-navigation-map": create_navigation_map(),
        "technical-architecture-and-patterns": create_architecture_guide(),
        
        # Operational knowledge
        "development-operations-guide": create_dev_ops_guide(),
        
        # Quick reference for efficiency
        "llm-quick-reference-index": create_quick_reference()

        # Historical context for evolution understanding
        "project-history-and-evolution": create_project_history()

        # Additional memories as needed
    }

    for name, content in memories.items():
        mcp_serena_write_memory(name, content)
```

### Cache Performance Optimization
```python
def optimize_memory_for_llm():
    # Structure for instant comprehension
    hierarchy = {
        'immediate_context': ['project-overview-and-status', 'llm-quick-reference-index'],
        'code_understanding': ['codebase-navigation-map', 'technical-architecture-and-patterns'],
        'operational': ['development-operations-guide']
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
- **Force reset:** `reset_llm_cache()`
- **Selective update:** `selective_cache_update(changed_files)`
- **Validation:** `validate_cache_consistency()`
- **Optimization:** `optimize_memory_for_llm_consumption()`

**REMEMBER:** The goal is complete LLM understanding - after reading memories, any LLM should fully comprehend the project's purpose, architecture, business logic, and be able to assist with development tasks effectively.
