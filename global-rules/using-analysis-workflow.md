# RULE 5: Problem Analysis & Solution Discovery Protocol

**GOAL:** Research deeply, analyze thoroughly, provide evidence-based solutions for ANY problem (technical or non-technical).

**WHEN TO USE:**
- User needs help finding solutions to a problem
- User wants to explore options before deciding
- User asks "what should I do?" or "how to solve X?"
- Before implementing ANY significant code/file changes

**CORE PRINCIPLE:** Never guess. Research depth should match problem complexity.

---

## STEP 0: ASSESS COMPLEXITY (First!)

**Quick Assessment:** Choose workflow based on:

| → 🟢 LIGHT Workflow | → 🔴 DEEP Workflow |
|---------------------|-------------------|
| Clear "how to" question | Architectural decision needed |
| Well-known pattern | Novel/unclear solution |
| Single component | Multi-component system |
| Low risk/impact | High risk/critical |
| Specific request | Vague/exploratory |

**When uncertain:** Start LIGHT, escalate to DEEP if needed (adaptive approach)
**Context savings:** Light = ~80% saved vs Deep = justified usage

---

## LIGHT WORKFLOW (Simple Problems) 🟢

**When:** Clear request, known patterns, low risk, single component

1. **Quick Check:** What's the core question? Known answer?
2. **Minimal Research** (1-2 tools max):
   - Library/framework → `context7_get_library_docs`
   - Code pattern → `exa_get_code_context`
   - General info → `brave_web_search`
3. **Direct Solution:** 1 approach + brief explanation + steps
4. **Validate:** Confirm with user if needed → Implement

**Response:** Direct answer → Why it works → Implementation steps

---

## DEEP WORKFLOW (Complex Problems) 🔴

**When:** Multi-component, high risk, unclear requirements, architectural decisions

### PHASE 1: PLAN & RESEARCH
- **Plan** (`sequential-thinking`): Break problem → identify unknowns → map research strategy
- **Multi-Source Research** (parallel execution):
  - `brave_web_search` → identify concepts/URLs
  - `Bright_Data_scrape_batch` → extract content (max 10 URLs)
  - `context7_get_library_docs` → official docs
  - `exa_get_code_context` + `octocode_*` → real-world patterns
- **Strategy**: Broad → Deep → Technical → Validate → Synthesize

### PHASE 2: DISCOVER ALTERNATIVES
- Find 2-3+ distinct approaches
- For each: Description, Pros/Cons, Complexity (H/M/L), Timeline, Dependencies, Best for

### PHASE 3: EVALUATE & DECIDE
- Define criteria (Performance, Maintainability, Time, etc.) + weights
- Score options (use `sequential-thinking`)
- **Recommend:** Chosen option + reasoning + confidence + risks/mitigation

### PHASE 4: VALIDATE & PLAN
- Confirm understanding with user
- Provide implementation roadmap:
  - IMMEDIATE (24h) → SHORT-TERM (1-7d) → MEDIUM-TERM (1-4w)
- Define success metrics + verification method

## RESPONSE TEMPLATE

**For LIGHT (adapt as needed):**
- Solution + Why it works + Implementation steps

**For DEEP (comprehensive):**
1. **Executive Summary:** Problem + Recommended solution + Key insight
2. **Research Insights:** Findings from each source (cited)
3. **Solution Options:** 2-3 alternatives (Description, Pros/Cons, Complexity, Timeline, Best for)
4. **Evaluation:** Scoring matrix → Recommended option + reasoning + confidence
5. **Roadmap:** Immediate/Short/Medium-term steps + Success metrics + Risks/mitigation

---

## VALIDATION CHECKLIST

**For LIGHT Workflow (Simple Problems):**
- [ ] **Complexity assessed** as SIMPLE with clear justification
- [ ] **Minimal research** completed (1-2 sources max)
- [ ] **Direct solution** provided with brief reasoning
- [ ] **Implementation steps** clear and actionable
- [ ] **User confirmation** if any uncertainty

**For DEEP Workflow (Complex Problems):**
- [ ] **Complexity assessed** as COMPLEX with clear justification
- [ ] **Research completed** from ≥3 sources (web search + content scrape + docs/code)
- [ ] **Problem decomposed** using sequential-thinking
- [ ] **≥2-3 alternatives** identified with pros/cons
- [ ] **Evidence-based** recommendation (all claims cited)
- [ ] **Evaluation criteria** defined and applied
- [ ] **Implementation plan** with timeline and success metrics
- [ ] **Risks identified** with mitigation strategies
- [ ] **User understanding** confirmed (ask questions if unclear)
- [ ] **Code citations** in format `startLine:endLine:filepath` (when applicable)
- [ ] **Parallel execution** used where possible (faster research)

---

## MCP TOOL QUICK REFERENCE

| Task | Primary Tool | When to Use | Light 🟢 | Deep 🔴 |
|------|-------------|-------------|---------|---------|
| Plan investigation | `sequential-thinking` | Structure approach | Brief | Detailed |
| General research | `brave_web_search` | Articles, discussions | ✓ | ✓ |
| Deep content | `Bright_Data_scrape_batch` | Extract from URLs (max 10) | ✗ | ✓ |
| Official docs | `context7_get_library_docs` | Authoritative sources | ✓ | ✓ |
| Code patterns | `exa_get_code_context` | Real-world examples | ✓ | ✓ |
| GitHub search | `octocode_githubSearchCode` | Find proven implementations | ✗ | ✓ |
| Full files | `octocode_githubGetFileContent` | Complete context | ✗ | ✓ |
| Repo structure | `octocode_githubViewRepoStructure` | Navigate projects | ✗ | ✓ |
| Quality repos | `octocode_githubSearchRepositories` | Discover by stars/topics | ✗ | ✓ |

**🟢 Light Workflow:** Use 1-2 tools max, minimal context  
**🔴 Deep Workflow:** Use 3+ tools, parallel execution for speed

---

## PRACTICAL EXAMPLES

**🟢 LIGHT:** "How to add timeout to Python requests?"
- Single library function, known pattern, low risk
- Action: `exa_get_code_context` → direct answer → done
- **Context saved: ~80%**

**🔴 DEEP:** "Best architecture for real-time analytics pipeline?"
- Multi-component, architectural decision, high risk
- Action: `sequential-thinking` + `brave_web_search` + `scrape_batch` + `context7` + `octocode` → compare 3 alternatives → detailed evaluation
- **Context used: justified by complexity**

**⚠️ UNCERTAIN:** "Optimize my database queries?"
- Start LIGHT: ask specifics → if clarified → escalate to DEEP
- **Better to start light and escalate than over-research**

---

**REMEMBER:** Context is expensive. Research smart, not hard. Match depth to complexity.
