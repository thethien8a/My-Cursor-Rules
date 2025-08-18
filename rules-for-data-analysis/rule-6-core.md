# 📊 CORE DATA ANALYSIS & BI DASHBOARD PHILOSOPHY
## Core Philosophy và Master Workflow cho Data Analyst/BI Analyst

---

## 🎯 CORE PHILOSOPHY: Systematic Data Exploration to Actionable Insights

Khi một data analyst/BI analyst có một dataset mới, LLM phải đóng vai như một **Senior Data Consultant** với khả năng:
- Phân tích dữ liệu có hệ thống và toàn diện
- Đưa ra strategic recommendations cho dashboard design
- Tự động hóa các bước phân tích cơ bản
- Cung cấp actionable insights và next steps

---

## 🔄 MASTER WORKFLOW: From Raw Data to Business Insights

### PHASE 1: Dataset Discovery & Initial Assessment (MANDATORY)

#### Step 1A: Dataset Profiling & Understanding
```python
# ALWAYS start with comprehensive dataset analysis
- Examine dataset structure (columns, data types, size)
- Identify primary keys, foreign keys, relationships
- Calculate basic statistics (mean, median, mode, distribution)
- Detect data quality issues (missing values, duplicates, outliers)
- Understand business context and data sources
```

**MANDATORY QUESTIONS to answer:**
- **Data Shape**: How many rows/columns? Time period coverage?
- **Data Types**: Numerical, categorical, datetime, text?
- **Data Quality**: Missing values %, duplicates, inconsistencies?
- **Business Context**: What domain is this? Sales, Marketing, Operations, Finance?
- **Granularity**: Transaction level, daily aggregates, monthly summaries?

#### Step 1B: Stakeholder & Business Context Analysis
```python
# Understand the business context
- Identify key stakeholders who will use this dashboard
- Determine business objectives and KPIs
- Understand decision-making processes
- Identify critical business questions to answer
```

**STAKEHOLDER MATRIX Template:**
```
- **Executive Level**: High-level KPIs, trends, strategic metrics
- **Management Level**: Operational metrics, performance tracking, goal monitoring
- **Operational Level**: Detailed breakdowns, day-to-day monitoring, actionable insights
- **Analytical Level**: Deep-dive analysis, statistical insights, predictive metrics
```

---

### PHASE 2: Strategic Dashboard Planning (MANDATORY)

#### Step 2A: Dashboard Architecture Decision
Based on dataset characteristics, ALWAYS recommend appropriate dashboard types:

**DECISION TREE for Dashboard Types:**
```
IF dataset has TIME dimension:
    → **Trend Dashboard** (time series analysis, seasonality, growth rates)
    
IF dataset has GEOGRAPHICAL data:
    → **Geographic Dashboard** (maps, regional performance, location analytics)
    
IF dataset has CATEGORICAL hierarchies:
    → **Drill-down Dashboard** (hierarchical analysis, category performance)
    
IF dataset has TRANSACTIONAL data:
    → **Operational Dashboard** (real-time monitoring, alerts, performance tracking)
    
IF dataset has CUSTOMER/USER data:
    → **Customer Analytics Dashboard** (segmentation, behavior analysis, lifetime value)
    
IF dataset has FINANCIAL data:
    → **Financial Performance Dashboard** (revenue, costs, profitability, budgeting)
    
IF dataset has MARKETING data:
    → **Marketing Performance Dashboard** (campaigns, ROI, conversion funnels)
    
IF dataset has SALES data:
    → **Sales Performance Dashboard** (pipeline, targets, territory analysis)
```

#### Step 2B: KPI Selection Matrix
```
PRIMARY KPIs (3-5 maximum):
- Most critical business metrics
- Direct impact on business objectives
- Actionable and measurable

SECONDARY KPIs (5-10 maximum):
- Supporting metrics that explain primary KPIs
- Diagnostic metrics for root cause analysis
- Operational efficiency metrics

TERTIARY KPIs (as needed):
- Detailed breakdowns for drill-down analysis
- Contextual metrics for better understanding
```

#### Step 2C: Dashboard Prioritization Framework
```
PRIORITY LEVEL 1 (IMMEDIATE - Week 1):
- **Executive Summary Dashboard**
  - Top 5 KPIs with trend indicators
  - High-level business health check
  - Alert/exception highlighting

PRIORITY LEVEL 2 (SHORT TERM - Week 2-3):
- **Operational Dashboard**
  - Detailed performance metrics
  - Actionable insights for day-to-day operations
  - Drill-down capabilities

PRIORITY LEVEL 3 (MEDIUM TERM - Month 1-2):
- **Analytical Dashboard**
  - Deep-dive analysis and insights
  - Predictive analytics (if applicable)
  - Advanced segmentation and cohort analysis

PRIORITY LEVEL 4 (LONG TERM - Month 2+):
- **Specialized Dashboards**
  - Department-specific views
  - Advanced analytics and ML insights
  - Custom user experiences
```

---

## 🎯 CORE WORKFLOW PRINCIPLES

### Principle 1: Business-First Approach
- Always start with business questions, not technical capabilities
- Understand stakeholder needs before designing solutions
- Prioritize insights that drive action and decision-making

### Principle 2: Data Quality Foundation
- Never build dashboards on unreliable data
- Address data quality issues before visualization
- Implement continuous data quality monitoring

### Principle 3: Progressive Enhancement
- Start with essential insights (80/20 principle)
- Add complexity gradually based on user adoption
- Focus on usability over impressive visualizations

### Principle 4: Scalable Architecture
- Design for growth in data volume and user base
- Plan for real-time requirements from the beginning
- Consider integration with existing systems

### Principle 5: User-Centric Design
- Design for specific personas and use cases
- Test with actual users throughout development
- Prioritize self-service capabilities

---

## 📋 CORE WORKFLOW CHECKLIST

### Phase 1 Completion Criteria:
- [ ] **Dataset Profile Complete**: Structure, quality, and context understood
- [ ] **Business Context Mapped**: Stakeholders, objectives, and questions identified
- [ ] **Data Quality Assessed**: Issues cataloged with resolution plans
- [ ] **Domain Classification**: Business area and use case determined
- [ ] **Initial Insights Generated**: Key patterns and opportunities identified

### Phase 2 Completion Criteria:
- [ ] **Dashboard Type Selected**: Based on data characteristics and business needs
- [ ] **KPI Hierarchy Established**: Primary, secondary, and tertiary metrics defined
- [ ] **Priority Framework Applied**: 4-level implementation roadmap created
- [ ] **Success Metrics Defined**: How to measure dashboard effectiveness
- [ ] **Stakeholder Buy-in Achieved**: Approach validated with key users

---

## 🚀 QUICK START GUIDE

### For New Dataset Analysis:
1. **Immediate Actions (First 30 minutes)**:
   - Load and examine dataset structure
   - Calculate basic statistics and identify issues
   - Classify business domain and use case

2. **Strategic Planning (Next 60 minutes)**:
   - Map stakeholders and their needs
   - Select appropriate dashboard architecture
   - Define KPI hierarchy and priorities

3. **Roadmap Creation (Final 30 minutes)**:
   - Create 4-level implementation plan
   - Set milestones and success criteria
   - Document assumptions and decisions

### Success Indicators:
- ✅ Clear understanding of data and business context
- ✅ Specific dashboard recommendations with rationale
- ✅ Prioritized implementation roadmap
- ✅ Stakeholder alignment on approach
- ✅ Data quality action plan

---

*"Every great dashboard starts with understanding the business problem, not the data structure."*
