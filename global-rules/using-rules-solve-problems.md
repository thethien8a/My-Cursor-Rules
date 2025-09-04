---
alwaysApply: true
---

# MANDATORY PRE-CODING ANALYSIS WORKFLOW RULES:

- **Goal**: Before solving problems, you must do multi‑source research, know clear structure and remember that before doing anything for me, making sure that you know what i really want to do by asking me questions till you understand my needs. And finally, give me all possible results/solutions based on your search/research on Internet and yourself.
- **No terminal**: Never run shell/CLI commands on your own.
- **Figma**: If any Figma URL appears → use the "Framelink Figma MCP".

## CRITICAL RULE: PROBLEM ANALYSIS BEFORE ANY CODE/FILE CHANGES

### **MANDATORY PRE-CODING WORKFLOW** 
Before ANY file editing, coding, or implementation work, you MUST complete this comprehensive analysis:

#### **Phase 1: Deep Understanding** (REQUIRED)
1. **Multi-Source Research**
   - **External Research:** Use at least 3 MCP tools to research on internet: brave-search + bright-data-mcp + context7 (prefer official docs; recent ≥ 2024)
   - **Internal Knowledge Integration:** Combine external research with your existing knowledge and expertise
   - **Synthesis:** Synthesize information from both external sources and internal knowledge to provide comprehensive analysis
   - **Planning:** Call sequential-thinking to plan research approach
   - **Execution:** Run tool calls in parallel; limit to 3–5 calls per batch

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

**COMPREHENSIVE PROBLEM ANALYSIS FORMAT:**
```
## Executive Summary
[Brief overview of the problem and recommended solution with key insights]

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
- **Timeline:** [Estimated time to implement]
- **Dependencies:** [What needs to be in place]
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
**Total Timeline:** [Estimated total time]
**Key Dependencies:** [What needs to be in place before starting]

1. **Immediate Actions (Next 24h):** [What to do first]
2. **Short-term (1-7 days):** [Detailed implementation steps]
3. **Medium-term (1-4 weeks):** [Ongoing tasks and milestones]
4. **Verification:** [How to confirm success]

## Success Metrics
- **Primary Success Indicator:** [Main metric to measure success]
- **Secondary Metrics:** [Additional metrics to track]
- **Measurement Timeline:** [When to measure and review]

## Risks & Considerations
- **Risk:** [Potential issue] → **Mitigation:** [How to address]
- **Risk:** [Potential issue] → **Mitigation:** [How to address]

## Additional Resources
- [Relevant documentation links]
- [Useful tools or libraries]

## Validation Checklist
- [ ] Problem fully understood with multi-source research
- [ ] At least 2-3 distinct alternatives identified and analyzed
- [ ] Clear pros/cons for each option documented
- [ ] Evidence-based recommendation with reasoning
- [ ] Implementation plan with clear timeline provided
- [ ] Success metrics defined and measurable
- [ ] Risks identified and mitigation strategies planned
- [ ] Dependencies clearly identified
```

**VALIDATION CHECKPOINTS:**
- [ ] Problem fully understood with multi-source research (brave-search + context7 + bright-data-mcp)
- [ ] Bright Data MCP used appropriately for web content analysis
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

1) **Plan (sequential‑thinking mcp)** - Now includes problem analysis planning
2) **Research (MCP search tool like: bright data mcp)** - Enhanced with systematic alternative discovery
3) **Validate (sequential-thinking mcp)** - Expanded to include solution validation and user confirmation
4) **Synthesize & Deliver** - Now uses structured response template

**REMEMBER: NO CODE CHANGES, FILE EDITS, OR IMPLEMENTATIONS until completing the full analysis above and receiving user confirmation of the approach.**
