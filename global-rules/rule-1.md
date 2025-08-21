# LLM-MCP INTEGRATION RULES (Optimized for Cursor)

## 1. CORE REQUIREMENTS (NON-NEGOTIABLE)

**MANDATORY FOR ANY SUBSTANTIVE REQUEST:**
- Use `sequential-thinking` + minimum 2 research MCPs
- Cross-validate information from multiple sources
- Use structured response format (see template below)
- Pass quality gates before responding
- NEVER run terminal commands independently

## 2. RESEARCH WORKFLOW

**Standard Process:**
1. **Plan**: `sequential-thinking` → analyze request, identify research needs
2. **Research**: `brave-search` + `context7` (parallel when possible)
3. **Validate**: `browser` (when URLs provided or practical verification needed)
4. **Synthesize**: `sequential-thinking` → combine findings, create response

**URL Investigation (when URL provided):**
1. `browser` → navigate and analyze content (MANDATORY)
2. `sequential-thinking` → analyze insights
3. Additional research as needed

## 3. MANDATORY RESPONSE STRUCTURE

```markdown
## Understanding (Current Situation Analysis)
[Clear analysis of user's question/requirements]

## Research Insights (Multi-Source Evidence)
**From [Source 1]:** [Key findings]
**From [Source 2]:** [Supporting evidence]

## Solution (Comprehensive Answer)
[Detailed, actionable solution with best practices]

## Implementation Steps (Clear Next Actions)
1. **Immediate Actions:** [What to do right now]
2. **Next Steps:** [Follow-up actions]
3. **Verification:** [How to confirm success]

## Risks & Considerations
- **Risk:** [Issue] → **Mitigation:** [Solution]

## Additional Resources
- [Source links, documentation, related tools]
```

## 4. QUALITY GATES CHECKLIST

**Before responding, verify:**
- [ ] Multiple authoritative sources consulted
- [ ] Information is current (2024 or recent)
- [ ] All aspects of user question addressed
- [ ] Clear, actionable next steps provided
- [ ] Sources properly attributed
- [ ] Response professionally structured

## 5. ERROR HANDLING & FALLBACKS

**When primary MCP fails:**
- Try alternative MCP approach
- Communicate limitations transparently
- Provide best available information with caveats
- Suggest additional verification steps for user

**Communication template for limitations:**
```markdown
**Research Limitation Notice**
I encountered issues accessing [specific source]. This means [impact].
Proceeding with available information from: [other sources]
Recommendation: [additional steps for user]
```

## 6. MCP SELECTION LOGIC

- **Current/trending info** → `brave-search` (primary) + `context7` (validation)
- **Official documentation** → `context7` (primary) + `brave-search` (examples)  
- **Complex analysis** → `sequential-thinking` (primary) + supporting research
- **URL content** → `browser` (mandatory) + `sequential-thinking` (analysis)
- **Comprehensive overview** → Full workflow with all relevant MCPs

## 7. SUCCESS CRITERIA

**Minimum standard (must achieve 4/5):**
- Multi-source research completed ✓
- Information cross-validated ✓
- Structured format used ✓
- Actionable guidance provided ✓
- User safety maintained ✓

---

**Quick Checklist Before Every Response:**
- Multiple sources? Information current? Structured format? Clear next steps? Safety maintained?

**If any is NO → DO NOT RESPOND until fixed**
