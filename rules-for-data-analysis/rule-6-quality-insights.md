# 🔍 DATA QUALITY & INSIGHTS GENERATION
## Data Quality Framework và Automated Insights Engine

---

## PHASE 5: Data Quality & Validation Framework (MANDATORY)

### Step 5A: Data Quality Checks
```python
MANDATORY_QUALITY_CHECKS = [
    "completeness_check",      # Missing values analysis
    "uniqueness_check",        # Duplicate detection
    "validity_check",          # Data format validation
    "consistency_check",       # Cross-field validation
    "accuracy_check",          # Business rule validation
    "timeliness_check",        # Data freshness validation
]

# Detailed Implementation
def comprehensive_data_quality_assessment(dataset):
    quality_report = {}
    
    # Completeness Analysis
    quality_report['completeness'] = {
        'missing_percentage': calculate_missing_percentages(),
        'critical_fields_missing': check_critical_fields(),
        'missing_patterns': analyze_missing_patterns(),
        'impact_assessment': assess_missing_data_impact()
    }
    
    # Uniqueness Analysis  
    quality_report['uniqueness'] = {
        'duplicate_records': find_duplicate_records(),
        'duplicate_percentage': calculate_duplicate_rate(),
        'key_field_uniqueness': check_primary_key_uniqueness(),
        'business_rule_violations': find_business_duplicates()
    }
    
    # Validity Analysis
    quality_report['validity'] = {
        'format_violations': check_data_formats(),
        'range_violations': check_value_ranges(),
        'type_mismatches': check_data_types(),
        'constraint_violations': check_business_constraints()
    }
    
    # Consistency Analysis
    quality_report['consistency'] = {
        'cross_field_consistency': check_field_relationships(),
        'temporal_consistency': check_time_series_consistency(),
        'reference_consistency': validate_foreign_keys(),
        'business_rule_consistency': validate_business_rules()
    }
    
    return quality_report
```

**DATA QUALITY SCORING FRAMEWORK:**
```
QUALITY SCORE CALCULATION:
- Completeness Weight: 25%
- Uniqueness Weight: 20%
- Validity Weight: 25%
- Consistency Weight: 20%
- Timeliness Weight: 10%

SCORE INTERPRETATION:
- 90-100: Excellent (Production Ready)
- 80-89: Good (Minor Issues to Address)
- 70-79: Fair (Significant Issues Present)
- 60-69: Poor (Major Data Quality Problems)
- <60: Critical (Data Not Suitable for Analysis)
```

### Step 5B: Statistical Validation
```python
STATISTICAL_VALIDATION = [
    "outlier_detection",       # Identify anomalies using IQR, Z-score, Isolation Forest
    "distribution_analysis",   # Understanding data spread, skewness, kurtosis
    "correlation_analysis",    # Relationship identification between variables
    "trend_analysis",          # Pattern recognition over time
    "seasonality_detection",   # Cyclical pattern identification
    "stationarity_testing",    # Time series stationarity checks
    "normality_testing",       # Distribution normality assessment
]

def advanced_statistical_analysis(dataset):
    stats_report = {}
    
    # Outlier Detection
    stats_report['outliers'] = {
        'iqr_outliers': detect_iqr_outliers(),
        'zscore_outliers': detect_zscore_outliers(),
        'isolation_forest': detect_anomalies_ml(),
        'business_outliers': detect_business_anomalies(),
        'outlier_impact': assess_outlier_business_impact()
    }
    
    # Distribution Analysis
    stats_report['distributions'] = {
        'normality_tests': test_normality_shapiro_ks(),
        'skewness_analysis': calculate_skewness_kurtosis(),
        'distribution_fitting': fit_probability_distributions(),
        'qq_plots': generate_quantile_plots()
    }
    
    # Correlation Analysis
    stats_report['correlations'] = {
        'pearson_correlations': calculate_pearson_correlation(),
        'spearman_correlations': calculate_spearman_correlation(),
        'correlation_significance': test_correlation_significance(),
        'multicollinearity': detect_multicollinearity()
    }
    
    # Time Series Analysis (if applicable)
    if has_time_dimension(dataset):
        stats_report['time_series'] = {
            'trend_analysis': decompose_time_series(),
            'seasonality_detection': detect_seasonal_patterns(),
            'stationarity_testing': test_stationarity_adf(),
            'autocorrelation': calculate_autocorrelation()
        }
    
    return stats_report
```

### Step 5C: Business Rule Validation
```python
BUSINESS_RULE_CATEGORIES = {
    "financial_rules": [
        "Revenue >= 0",
        "Discount <= Original_Price", 
        "Total_Cost = Sum_of_Components",
        "Profit = Revenue - Costs"
    ],
    "temporal_rules": [
        "End_Date >= Start_Date",
        "Created_Date <= Modified_Date",
        "Transaction_Date within Business_Hours",
        "Future_Dates for Forecasting Only"
    ],
    "categorical_rules": [
        "Status in ['Active', 'Inactive', 'Pending']",
        "Category matches Product_Hierarchy", 
        "Region valid for Country",
        "Department exists in Organization"
    ],
    "relationship_rules": [
        "Customer_ID exists in Customer_Table",
        "Product_ID exists in Product_Table",
        "One-to-Many relationships maintained",
        "Parent-Child hierarchies valid"
    ]
}

def validate_business_rules(dataset, domain):
    validation_results = {}
    
    for rule_category, rules in BUSINESS_RULE_CATEGORIES.items():
        validation_results[rule_category] = []
        
        for rule in rules:
            result = {
                'rule': rule,
                'violations': find_rule_violations(dataset, rule),
                'violation_percentage': calculate_violation_rate(dataset, rule),
                'business_impact': assess_rule_impact(rule),
                'recommended_action': suggest_remediation(rule)
            }
            validation_results[rule_category].append(result)
    
    return validation_results
```

---

## PHASE 6: Business Intelligence & Insights Generation (MANDATORY)

### Step 6A: Automated Insights Engine
```python
def generate_automatic_insights(dataset):
    insights = []
    
    # Trend Analysis Insights
    trend_insights = analyze_trends(dataset)
    insights.extend([
        detect_growth_trends(),
        identify_seasonality_patterns(),
        find_cyclical_behaviors(),
        predict_future_trends(),
        detect_trend_changes()
    ])
    
    # Comparative Analysis Insights  
    comparison_insights = comparative_analysis(dataset)
    insights.extend([
        period_over_period_comparison(),
        segment_performance_analysis(),
        geographic_performance_variance(),
        product_category_comparison(),
        cohort_performance_analysis()
    ])
    
    # Anomaly Detection Insights
    anomaly_insights = detect_anomalies(dataset)
    insights.extend([
        statistical_outliers(),
        business_rule_violations(),
        unusual_patterns(),
        performance_alerts(),
        data_quality_issues()
    ])
    
    # Performance Insights
    performance_insights = analyze_performance(dataset)
    insights.extend([
        top_performers_identification(),
        underperformance_analysis(),
        efficiency_opportunities(),
        benchmark_comparisons(),
        goal_achievement_status()
    ])
    
    # Predictive Insights
    if suitable_for_prediction(dataset):
        predictive_insights = generate_predictions(dataset)
        insights.extend([
            forecast_next_period(),
            identify_leading_indicators(),
            risk_assessment(),
            scenario_analysis(),
            recommendation_engine()
        ])
    
    return prioritize_insights(insights)

def prioritize_insights(insights):
    """Priority scoring based on business impact and confidence"""
    for insight in insights:
        insight['priority_score'] = (
            insight['business_impact'] * 0.4 +
            insight['statistical_confidence'] * 0.3 +
            insight['actionability'] * 0.2 +
            insight['novelty'] * 0.1
        )
    
    return sorted(insights, key=lambda x: x['priority_score'], reverse=True)
```

### Step 6B: Narrative Generation Template
```
INSIGHT NARRATIVE STRUCTURE:

**📈 KEY FINDING**: [Clear, actionable insight in one sentence]

**📊 SUPPORTING DATA**: 
- Specific numbers and percentages with context
- Trend direction and magnitude over time periods
- Statistical significance and confidence levels
- Comparison to benchmarks or targets

**🔍 BUSINESS IMPACT**:
- What this means for business objectives
- Potential revenue/cost/efficiency implications
- Risk assessment and opportunity identification
- Stakeholder groups most affected

**📋 RECOMMENDED ACTIONS**:
- Immediate actions (next 1-2 weeks)
- Short-term initiatives (next 1-3 months)
- Long-term strategic changes (3+ months)
- Specific owners and timelines

**🎯 SUCCESS METRICS**:
- KPIs to monitor progress
- Expected impact quantification
- Timeline for expected results
- Validation methods

**⚠️ RISKS & CONSIDERATIONS**:
- Potential risks of action/inaction
- Resource requirements and constraints
- Dependencies on other initiatives
- Alternative approaches to consider
```

### Step 6C: Insight Categories & Templates
```python
INSIGHT_TEMPLATES = {
    "trend_insight": {
        "template": "{metric} has {trend_direction} by {percentage}% over {time_period}, {trend_context}",
        "examples": [
            "Revenue has increased by 15% over the last quarter, accelerating from 8% growth in the previous quarter",
            "Customer churn has decreased by 23% over the past 6 months, the lowest rate in 2 years"
        ]
    },
    
    "comparison_insight": {
        "template": "{segment_a} {comparison_verb} {segment_b} by {difference} in {metric}",
        "examples": [
            "Enterprise customers outperform SMB customers by 45% in average contract value",
            "West region underperforms East region by 12% in sales conversion rates"
        ]
    },
    
    "anomaly_insight": {
        "template": "{metric} shows {anomaly_type} behavior in {time_period}, {deviation_context}",
        "examples": [
            "Website traffic shows unusual spike behavior in March 2024, 3.2 standard deviations above normal",
            "Manufacturing defect rate shows concerning increase in Week 12, breaking 6-month downward trend"
        ]
    },
    
    "correlation_insight": {
        "template": "{variable_a} and {variable_b} show {correlation_strength} {correlation_direction} correlation ({correlation_coefficient})",
        "examples": [
            "Marketing spend and lead generation show strong positive correlation (r=0.78)",
            "Customer satisfaction and support response time show moderate negative correlation (r=-0.65)"
        ]
    },
    
    "opportunity_insight": {
        "template": "Opportunity identified in {area}: {opportunity_description} with potential {impact_estimate}",
        "examples": [
            "Opportunity identified in customer retention: targeting at-risk customers could prevent $2M in annual churn",
            "Opportunity identified in inventory optimization: reducing overstock could free up $500K in working capital"
        ]
    }
}
```

### Step 6D: Advanced Analytics Integration
```python
ADVANCED_ANALYTICS_CAPABILITIES = {
    "statistical_modeling": {
        "regression_analysis": "Understand relationships between variables",
        "cluster_analysis": "Segment customers/products/regions",
        "classification": "Predict categorical outcomes",
        "survival_analysis": "Analyze time-to-event data"
    },
    
    "machine_learning": {
        "anomaly_detection": "Identify unusual patterns automatically",
        "recommendation_systems": "Suggest next best actions",
        "forecasting_models": "Predict future performance", 
        "optimization": "Find optimal resource allocation"
    },
    
    "text_analytics": {
        "sentiment_analysis": "Analyze customer feedback sentiment",
        "topic_modeling": "Extract key themes from text data",
        "entity_extraction": "Identify important entities in text",
        "text_classification": "Categorize documents automatically"
    },
    
    "network_analysis": {
        "customer_journey": "Map customer interaction paths",
        "influence_analysis": "Identify key influencers",
        "community_detection": "Find natural groupings",
        "centrality_measures": "Identify most important nodes"
    }
}

def suggest_advanced_analytics(dataset_characteristics):
    suggestions = []
    
    if has_customer_data(dataset_characteristics):
        suggestions.append("Customer segmentation using clustering")
        suggestions.append("Customer lifetime value prediction")
        suggestions.append("Churn prediction modeling")
    
    if has_time_series_data(dataset_characteristics):
        suggestions.append("Automated forecasting with confidence intervals")
        suggestions.append("Seasonal decomposition and trend analysis")
        suggestions.append("Anomaly detection in time series")
    
    if has_text_data(dataset_characteristics):
        suggestions.append("Sentiment analysis of customer feedback")
        suggestions.append("Topic modeling for theme extraction")
        suggestions.append("Automated text classification")
    
    if has_transactional_data(dataset_characteristics):
        suggestions.append("Market basket analysis")
        suggestions.append("Recommendation system development")
        suggestions.append("Fraud detection modeling")
    
    return suggestions
```

---

## 🎯 DATA QUALITY & INSIGHTS SUCCESS METRICS

### Data Quality Metrics:
- **Overall Quality Score**: > 85/100 for production use
- **Critical Field Completeness**: > 95% for key business fields
- **Duplicate Rate**: < 2% for transactional data
- **Business Rule Compliance**: > 98% for critical rules
- **Data Freshness**: Meets defined SLA requirements

### Insight Generation Metrics:
- **Insight Relevance**: > 80% of insights rated as relevant by users
- **Insight Actionability**: > 70% of insights lead to concrete actions
- **Prediction Accuracy**: > 80% accuracy for forecasting models
- **Discovery Rate**: Identify 5+ significant insights per dataset
- **Time to Insight**: Generate initial insights within 2 hours

### Business Impact Metrics:
- **Decision Speed**: 50% faster decision-making with insights
- **Action Rate**: 60% of recommended actions implemented
- **ROI from Insights**: Positive ROI within 6 months
- **User Adoption**: 75% of stakeholders regularly use insights
- **Insight Accuracy**: < 10% false positive rate for recommendations

---

*"Data quality is not negotiable – reliable insights can only come from reliable data."*
