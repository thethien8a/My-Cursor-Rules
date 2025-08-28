---
alwaysApply: true
---

# SOLVING PROBLEMS RULES:

- **Goal**: Before doing anything, you must do multi‑source research, know clear structure, and concrete actions.
- **No terminal**: Never run shell/CLI commands on your own.
- **Figma**: If any Figma URL appears → use the "Framelink Figma MCP".

## CRITICAL RULE: PROBLEM ANALYSIS BEFORE ANY CODE/FILE CHANGES

### **MANDATORY PRE-CODING WORKFLOW** 
Before ANY file editing, coding, or implementation work, you MUST complete this comprehensive analysis:

#### **Phase 1: Deep Understanding** (REQUIRED)
1. **Multi-Source Research**
   - Use at least 2 sources: brave-search + context7 (prefer official docs; recent ≥ 2024)
   - Call sequential-thinking to plan research approach
   - Run tool calls in parallel; limit to 3–5 calls per batch

2. **Problem Decomposition** 
   - Use sequential-thinking mcp to break down the problem
   - Break down the request into core components
   - Identify dependencies and relationships
   - Map out the problem domain and constraints
   - Document assumptions and unknowns

3. **Context Analysis**
   - Understand project structure and existing patterns
   - Identify relevant files, frameworks, and conventions
   - Assess impact scope (local vs system-wide changes)

#### **Phase 2: Solution Discovery** (REQUIRED)
4. **Alternative Identification**
   - Research ALL feasible approaches to solve the problem
   - Include both conventional and innovative solutions
   - Consider different architectural patterns, libraries, or methodologies
   - Document minimum 2-3 distinct approaches

5. **Feasibility Analysis**
   - Technical feasibility (complexity, time, resources)
   - Compatibility with existing system
   - Performance implications
   - Maintenance and scalability considerations

#### **Phase 3: Decision Framework** (REQUIRED)
6. **Multi-Criteria Evaluation**
   - Define evaluation criteria (performance, maintainability, complexity, time-to-implement)
   - Score each alternative against criteria
   - Weight criteria based on project priorities

7. **Pros & Cons Analysis**
   - Detailed advantages of each approach
   - Specific disadvantages and limitations
   - Risk assessment and mitigation strategies
   - Long-term implications

8. **Recommendation with Reasoning**
   - State clearly which approach is recommended
   - Provide detailed reasoning based on evaluation
   - Explain why this approach is optimal for the specific context
   - Include confidence level and caveats

#### **Phase 4: Implementation Readiness** (REQUIRED)
9. **Understanding Validation**
   - Confirm user's problem is fully understood
   - Verify recommended approach aligns with user's goals
   - Ask clarifying questions if any ambiguity remains

10. **Implementation Plan**
    - Break down implementation into clear steps
    - Identify potential challenges and solutions
    - Estimate effort and timeline
    - Define success criteria and testing approach

### **Quality Gates & Response Template**

**MANDATORY RESPONSE FORMAT:**
```
## Understanding (Current Situation Analysis)
[Comprehensive problem analysis and context]

## Research Insights (Multi-Source Evidence)
**From [Source 1]:** [Key findings with citations]
**From [Source 2]:** [Supporting evidence with citations]

## Solution Alternatives (All Feasible Approaches)
### Option 1: [Name]
- **Description:** [Detailed explanation]
- **Pros:** [Specific advantages]
- **Cons:** [Specific limitations]
- **Complexity:** [Assessment]
- **Best for:** [Use cases]

### Option 2: [Name]
[Same structure as Option 1]

### Option 3: [Name]
[Same structure as Option 1]

## Decision Framework (Evaluation & Recommendation)
**Evaluation Criteria:**
- [Criterion 1]: Weight [X%]
- [Criterion 2]: Weight [Y%]
- [Criterion 3]: Weight [Z%]

**Scoring Matrix:**
| Option | Criterion 1 | Criterion 2 | Criterion 3 | Total Score |
|--------|-------------|-------------|-------------|-------------|
| Option 1 | [Score] | [Score] | [Score] | [Total] |
| Option 2 | [Score] | [Score] | [Score] | [Total] |

**RECOMMENDATION:** [Chosen Option]
**REASONING:** [Detailed explanation why this option is optimal]
**CONFIDENCE LEVEL:** [High/Medium/Low with justification]

## Implementation Plan (Clear Next Actions)
1. **Immediate Actions:** [What to do first]
2. **Step-by-step Process:** [Detailed implementation steps]
3. **Verification:** [How to confirm success]

## Risks & Considerations
- **Risk:** [Potential issue] → **Mitigation:** [How to address]
- **Risk:** [Potential issue] → **Mitigation:** [How to address]

## Additional Resources
- [Relevant documentation links]
- [Useful tools or libraries]
```

**VALIDATION CHECKPOINTS:**
- [ ] Problem fully understood with multi-source research
- [ ] At least 2-3 distinct alternatives identified and analyzed
- [ ] Clear pros/cons for each option documented
- [ ] Evidence-based recommendation with reasoning
- [ ] User understanding confirmed before implementation
- [ ] Implementation plan with clear steps provided

**QUALITY STANDARDS:**
- **Thoroughness:** Cover all aspects of the problem domain
- **Evidence-Based:** All claims supported by research and citations
- **Clarity:** Technical concepts explained clearly
- **Actionability:** Provide concrete, implementable solutions
- **Risk Awareness:** Identify and address potential issues

### **Standard Workflow Integration**
The above PRE-CODING WORKFLOW integrates with the existing standard workflow:

1) **Plan (sequential‑thinking)** - Now includes problem analysis planning
2) **Research (parallel)** - Enhanced with systematic alternative discovery
3) **Validate** - Expanded to include solution validation and user confirmation
4) **Synthesize & Deliver** - Now uses structured response template

**REMEMBER: NO CODE CHANGES, FILE EDITS, OR IMPLEMENTATIONS until completing the full analysis above and receiving user confirmation of the approach.**
