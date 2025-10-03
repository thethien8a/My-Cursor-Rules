# RULE 6: Serena MCP Memory Management Rule

**When use this rule**: 
- When user ask "update memory" or "cập nhật memory"
- When you think that "that changes in code have much impact on current project"

**OBJECTIVE:** To define the structure and workflow for creating and maintaining the project's knowledge base using Serena's memory tools.

---

## 1. The Memory Lifecycle (Mandatory Workflow)

### Phase 1: Onboarding (First-time analysis)
1.  **Activate Project:** `mcp_serena_activate_project(...)`
2.  **Check Onboarding:** `mcp_serena_check_onboarding_performed()`
3.  **If not onboarded, create core memories:**
    - Apply the investigation workflow from `rule4.md` to the codebase.
    - Synthesize findings and use `mcp_serena_write_memory` to create the initial versions of the 6 core documents listed below.

### Phase 2: Daily Operations (Read → Analyze → Update)
1.  **READ:** Before starting any task, `read_memory` to load context. Start with `project-overview-and-status`.
2.  **ANALYZE:** Use Serena's symbol-level tools (`find_symbol`, `find_referencing_symbols`) to investigate the code, guided by the memory.
3.  **UPDATE:** After discovering new information (architectural patterns, key dependencies, "gotchas"), you **must** update the relevant memory document using `write_memory`.

---

## 2. The 8 Core Memory Documents

*These are the mandatory files that form the project's knowledge base.*

#### 1. `project-overview-and-status`
- **Key Sections:** Project Purpose, Tech Stack, Current Status, Active Work, Decision Log.
- **Build With:** `README.md`, project configs, manual synthesis.

#### 2. `codebase-navigation-map`
- **Key Sections:** Repository Structure, Main Entry Points, Key Module summaries, Navigation Shortcuts.
- **Build With:** `list_dir`, `get_symbols_overview`.

#### 3. `technical-architecture-and-patterns`
- **Key Sections:** High-Level Architecture Diagram/Description, Core Components, Data Flow, Key Implementation Patterns.
- **Build With:** `find_symbol`, `find_referencing_symbols`, targeted `read_file`.

#### 4. `development-operations-guide`
- **Key Sections:** Quick Start Commands, Local Setup, Testing Procedures, Deployment Workflow.
- **Build With:** `read_file` on `docker-compose.yml`, `requirements.txt`, CI/CD files.

#### 5. `llm-quick-reference-index`
- **Key Sections:** Index of Critical Symbols, Key APIs, Common "Gotchas", Important Configuration Variables.
- **Build With:** Continuous updates from the "UPDATE" step in daily operations.

#### 6. `project-history-and-evolution`
- **Key Sections:** Timeline of Major Milestones, Lessons Learned from past refactors.
- **Build With:** Git history, PR descriptions, and major task summaries.

#### 7. `business-context-and-domain-knowledge.md`
- **Key Sections:** Core Business Problem, Target Audience/User Personas, Key Business Workflows, Domain-Specific Glossary.
- **Build With:** Product documentation, user stories, interviews with stakeholders.

#### 8. `testing-strategy-and-quality-assurance.md`
- **Key Sections:** Testing Philosophy, Tooling and Frameworks, How to Run Tests, Key Test Scenarios.
- **Build With:** `read_file` on testing configs, CI files, and analyzing existing test suites.

---

## 3. Handoff Protocol (for multi-session tasks)

- At the end of a session on a long-running task, create a temporary handoff memory.
- **Name:** `handoff-[feature-name]-[YYYY-MM-DD]`
- **Content:** Summarize status, next steps, and any blockers.
- The next LLM session **must** start by reading this handoff memory.
