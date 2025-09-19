# RULE 2: Mandatory Analysis Workflow

- Always analyze before any code change.
- External research: Brave search → Bright Data scrape → Context7 docs → OctoCode GitHub evidence.
- Decompose problem; map dependencies and context.
- Use Serena for symbol-aware discovery/edits; Cursor for exact search/diagnostics.
- Propose alternatives; pick with clear criteria.
- Make minimal, safe edits; verify with lints/tests; document in memories.

---

**GOAL:** Before solving problems, you must do multi-source research, know clear structure and remember that before doing anything for me, making sure that you know what i really want to do by asking me questions till you understand my needs. And finally, give me all possible results/solutions based on your search/research on Internet and yourself.

## WHEN IS THIS RULE APPLIED ?
1. When fix errors/bug in code
2. When you find any solutions for any problem user asks

---

## CRITICAL RULE: PROBLEM ANALYSIS BEFORE ANY CODE/FILE CHANGES/ANSWER THE QUESTIONS FROM USER

### MANDATORY PRE-CODING WORKFLOW

Before ANY file editing, coding, or implementation work, you MUST complete this comprehensive analysis:

### PHASE 1: DEEP UNDERSTANDING (REQUIRED)

#### 1. MULTI-SOURCE RESEARCH
*   **EXTERNAL RESEARCH:** Use at least 3 MCP tools to research on internet: brave-search + Bright Data mcp (scrape-batch tool) + context7 (prefer official docs; recent ≥ 2024)
    *   First: using brave-search to search to find the most relevant information on internet
    *   Second: using Bright Data mcp: scrape-batch tool to fetch all urls after you search by brave-search on internet (scrape 4-5 urls) (for more details)
    *   Third: using context7 to fetch the library/docs for coding task
    *   Fourth: using OctoCode MCP for GitHub code research (implementation-first evidence)
        *   When to use: whenever the task requires real code patterns, examples, or cross-repo comparisons. Prefer OctoCode over general web search for code-level answers.
        *   Core tools:
            - `githubSearchCode` (progressive queries; multiple angles in parallel)
            - `githubViewRepoStructure` (understand layout; `path` + `depth`)
            - `githubGetFileContent` (targeted sections via `startLine`/`endLine` or `matchString` with context)
            - `githubSearchRepositories` (discover high-quality repos; filter by `language`, `stars`, `updated`)
        *   Recommended usage:
            - Start broad with 2-4 progressive `githubSearchCode` queries (semantic term, exact API/class, file pattern, topic+language) and run them in parallel.
            - Narrow down with `githubViewRepoStructure`, then fetch exact files/sections using `githubGetFileContent` with `matchStringContextLines`.
            - Cite evidence with owner/repo/path and relevant lines. Prefer popular/maintained repos (`stars`, `updated`).
*   **INTERNAL KNOWLEDGE INTEGRATION:** Combine external research with your existing knowledge and expertise
*   **SYNTHESIS:** Synthesize information from both external sources and internal knowledge to provide comprehensive analysis
*   **PLANNING:** Call sequential-thinking to plan research approach

#### 2. PROBLEM DECOMPOSITION
*   Use sequential-thinking mcp to break down the problem
*   Break down the request into core components
*   Identify dependencies and relationships
*   Map out the problem domain and constraints
*   Document assumptions and unknowns

#### 3. CONTEXT ANALYSIS
*   Understand project structure and existing patterns
*   Identify relevant files, frameworks, and conventions
*   Assess impact scope (local vs system-wide changes)

#### OctoCode MCP Integration (GitHub code research)
*   Purpose: Supercharge analysis with real-world, production-grade code patterns from GitHub. Move beyond documentation and see how top projects implement solutions.
*   Tool mappings & patterns:
    - Discovery → `githubSearchRepositories` (filters: `topic`, `language`, `stars`, `updated`)
    - Code search → `githubSearchCode` (use several narrowly focused queries in parallel; set `limit` 5–10)
    - Repo overview → `githubViewRepoStructure` (use `depth` 1–2; drill into `path` as needed)
    - Targeted reading → `githubGetFileContent` (prefer `matchString` + `matchStringContextLines` 5–15; or `startLine`/`endLine` for large files; set `minified` true)
*   Best practices:
    - Run independent OctoCode queries in parallel to reduce latency.
    - Prefer authoritative repos (high stars, recent `pushed/updated`).
    - Always include precise citations: `owner/repo` + file path + relevant section.
    - Compare multiple implementations to identify common patterns, trade-offs, and best practices.
    - For private orgs, require explicit permission and ensure tokens are scoped least-privilege. Keep tokens in environment, never inline.
    - Use OctoCode as primary source for implementation details; use Context7 for official docs and Brave/Bright Data for web context.

---

### PHASE 2: SOLUTION DISCOVERY (REQUIRED)

#### 4. ALTERNATIVE IDENTIFICATION
*   Research ALL feasible approaches to solve the problem
*   Include both conventional and innovative solutions
*   Consider different architectural patterns, libraries, or methodologies
*   Document minimum 2-3 distinct approaches

#### 5. FEASIBILITY ANALYSIS
*   Technical feasibility (complexity, time, resources)
*   Compatibility with existing system
*   Performance implications
*   Maintenance and scalability considerations

---

### PHASE 3: DECISION FRAMEWORK (REQUIRED)

#### 6. MULTI-CRITERIA EVALUATION
*   Define evaluation criteria (performance, maintainability, complexity, time-to-implement)
*   Score each alternative against criteria
*   Weight criteria based on project priorities

#### 7. PROS & CONS ANALYSIS
*   Detailed advantages of each approach
*   Specific disadvantages and limitations
*   Risk assessment and mitigation strategies
*   Long-term implications

#### 8. RECOMMENDATION WITH REASONING
*   State clearly which approach is recommended
*   Provide detailed reasoning based on evaluation
*   Explain why this approach is optimal for the specific context
*   Include confidence level and caveats

---

### PHASE 4: IMPLEMENTATION READINESS (REQUIRED)

#### 9. UNDERSTANDING VALIDATION
*   Confirm user's problem is fully understood
*   Verify recommended approach aligns with user's goals
*   Ask clarifying questions if any ambiguity remains

#### 10. IMPLEMENTATION PLAN
*   Break down implementation into clear steps
*   Identify potential challenges and solutions
*   Estimate effort and timeline
*   Define success criteria and testing approach

---

## QUALITY GATES & RESPONSE TEMPLATE

### COMPREHENSIVE PROBLEM ANALYSIS FORMAT:

**EXECUTIVE SUMMARY**
[Brief overview of the problem and recommended solution with key insights]

**UNDERSTANDING (CURRENT SITUATION ANALYSIS)**
[Comprehensive problem analysis and context]

**RESEARCH INSIGHTS (MULTI-SOURCE EVIDENCE)**
*   FROM [SOURCE 1]: [Key findings with citations]
*   FROM [SOURCE 2]: [Supporting evidence with citations]

**SOLUTION ALTERNATIVES (ALL FEASIBLE APPROACHES)**

**OPTION 1: [NAME]**
*   **DESCRIPTION:** [Detailed explanation]
*   **PROS:** [Specific advantages]
*   **CONS:** [Specific limitations]
*   **COMPLEXITY:** [Assessment]
*   **TIMELINE:** [Estimated time to implement]
*   **DEPENDENCIES:** [What needs to be in place]
*   **BEST FOR:** [Use cases]

**OPTION 2: [NAME]**
[Same structure as Option 1]

**OPTION 3: [NAME]**
[Same structure as Option 1]

**DECISION FRAMEWORK (EVALUATION & RECOMMENDATION)**

**EVALUATION CRITERIA:**
*   [Criterion 1]: Weight [X%]
*   [Criterion 2]: Weight [Y%]
*   [Criterion 3]: Weight [Z%]

**SCORING MATRIX:**
```
OPTION    CRITERION 1    CRITERION 2    CRITERION 3    TOTAL SCORE
--------  -------------  -------------  -------------  -------------
Option 1  [Score]        [Score]        [Score]        [Total]
Option 2  [Score]        [Score]        [Score]        [Total]
```

**RECOMMENDATION:** [Chosen Option]
**REASONING:** [Detailed explanation why this option is optimal]
**CONFIDENCE LEVEL:** [High/Medium/Low with justification]

**IMPLEMENTATION PLAN (CLEAR NEXT ACTIONS)**

**TOTAL TIMELINE:** [Estimated total time]
**KEY DEPENDENCIES:** [What needs to be in place before starting]

1.  **IMMEDIATE ACTIONS (NEXT 24H):** [What to do first]
2.  **SHORT-TERM (1-7 DAYS):** [Detailed implementation steps]
3.  **MEDIUM-TERM (1-4 WEEKS):** [Ongoing tasks and milestones]
4.  **VERIFICATION:** [How to confirm success]

**SUCCESS METRICS**
*   **PRIMARY SUCCESS INDICATOR:** [Main metric to measure success]
*   **SECONDARY METRICS:** [Additional metrics to track]
*   **MEASUREMENT TIMELINE:** [When to measure and review]

**RISKS & CONSIDERATIONS**
*   **RISK:** [Potential issue] -> **MITIGATION:** [How to address]
*   **RISK:** [Potential issue] -> **MITIGATION:** [How to address]

**ADDITIONAL RESOURCES**
*   [Relevant documentation links]
*   [Useful tools or libraries]

---

### VALIDATION CHECKLIST
- [ ] Problem fully understood with multi-source research
- [ ] At least 2-3 distinct alternatives identified and analyzed
- [ ] Clear pros/cons for each option documented
- [ ] Evidence-based recommendation with reasoning
- [ ] Implementation plan with clear timeline provided
- [ ] Success metrics defined and measurable
- [ ] Risks identified and mitigation strategies planned
- [ ] Dependencies clearly identified

### VALIDATION CHECKPOINTS:
- [ ] Problem fully understood with multi-source research (brave-search for search web + bright data mcp for scrape multiple sites + context7 for search docs)
- [] Using brave search mcp and scrape_batch_url by using Bright Data mcp to get the specific informations
- [ ] At least 2-3 distinct alternatives identified and analyzed
- [ ] Clear pros/cons for each option documented
- [ ] Evidence-based recommendation with reasoning
- [ ] User understanding confirmed before implementation
- [ ] Implementation plan with clear steps provided

### QUALITY STANDARDS:
*   **THOROUGHNESS:** Cover all aspects of the problem domain
*   **EVIDENCE-BASED:** All claims supported by research and citations
*   **CLARITY:** Technical concepts explained clearly
*   **ACTIONABILITY:** Provide concrete, implementable solutions
*   **RISK AWARENESS:** Identify and address potential issues

---

## STANDARD WORKFLOW INTEGRATION

The above PRE-CODING WORKFLOW integrates with the existing standard workflow:

1.  **PLAN (SEQUENTIAL-THINKING MCP)** - Now includes problem analysis planning
2.  **RESEARCH (MCP SEARCH TOOL LIKE: BRAVE-SEARCH FOR SEARCH WEB + BRIGHT DATA MCP FOR SCRAPE MULTIPLE SITES + CONTEXT7 FOR SEARCH DOCS)**
3.  **VALIDATE (SEQUENTIAL-THINKING MCP)** - Expanded to include solution validation and user confirmation
4.  **SYNTHESIZE & DELIVER** - Now uses structured response template

**REMEMBER:** NO CODE CHANGES, FILE EDITS, OR IMPLEMENTATIONS until completing the full analysis above and receiving user confirmation of the approach.
