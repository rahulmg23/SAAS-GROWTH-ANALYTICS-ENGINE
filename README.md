# SAAS-GROWTH-ANALYTICS-ENGINE



> **End-to-end product analytics implementation** — from raw event data to executive insights that drive revenue.

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue)](https://python.org)
[![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-orange)](https://pandas.pydata.org)
[![Mixpanel](https://img.shields.io/badge/Mixpanel-Analytics-purple)](https://mixpanel.com)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## Executive Dashboard

<img width="655" height="443" alt="Screenshot 2026-06-19 222148" src="https://github.com/user-attachments/assets/6111a654-55e3-4418-a119-b11bad8461c7" />


*6-chart analytics dashboard showing KPIs, onboarding funnel, channel quality, cohort retention, LTV:CAC ratios, and revenue projections.*

---

## Table of Contents

- [Project Overview](#-project-overview)
- [Business Problem](#-business-problem)
- [Key Insights](#-key-insights)
- [Technical Implementation](#-technical-implementation)
- [Analytics Stack](#-analytics-stack)
- [Data Model](#-data-model)
- [Results & Impact](#-results--impact)
- [Files & Deliverables](#-files--deliverables)
- [How to Run](#-how-to-run)
- [What I Learned](#-what-i-learned)
- [Connect With Me](#-connect-with-me)

---

## Project Overview

**Product:** TaskFlow — Project Management SaaS  
**Role:** Data Analyst (Product Analytics)  
**Dataset:** 1,964 events across 500 users over 45 days  

### Objective
Design and implement a complete analytics stack to understand user acquisition, activation, and retention patterns — and translate findings into actionable business recommendations with projected revenue impact.

---

##  Business Problem

TaskFlow was experiencing:
- **High signup volume** but low activation
- **Unknown channel quality** — spending on ads without knowing ROI
- **Churn without understanding** why users leave
- **No data-driven onboarding optimization**

**The Question:** *Where is the biggest leak in our growth funnel, and how do we fix it?*

---

##  Key Insights

### 1. Onboarding Funnel Leak 

| Step | Users | Conversion | Drop-off |
|------|-------|-----------|----------|
| Signed Up | 500 | 100% | — |
| Onboarding Started | 412 | 82.4% | -88 users |
| **Onboarding Completed** | **248** | **49.6%** | **-164 users** |

**Finding:** 50% of all signups never complete onboarding. The biggest leak is Step 2→3.

**Recommendation:** Simplify onboarding to 3 steps, add progress indicators, send email reminders to abandoners.

**Impact:** +15% activation = +48 users/month = **₹1.7L/year additional MRR**

---

### 2. Channel Quality Gap 

| Channel | Users | Activation Rate | Churn Rate | LTV:CAC Ratio |
|---------|-------|----------------|-----------|---------------|
| **Referral** | 81 | 3.7% | 7.4% | **4.7x**  |
| Facebook | 93 | 3.2% | 17.2% | 2.6x |
| LinkedIn | 49 | 10.2% | 24.5% | 1.3x |
| Google Ads | 134 | 5.2% | 21.6% | **0.9x**  |
| Organic | 143 | 2.1% | 15.4% | ∞ (free) |

**Finding:** Google Ads is burning money (0.9x LTV:CAC). Referral is the goldmine (4.7x).

**Recommendation:** Shift 20% of Google Ads budget to Referral program. Audit Facebook targeting.

**Impact:** Reallocate ₹40K/month ad spend = +30% overall retention = **₹4.8L/year saved + earned**

---

### 3. Cohort Retention Patterns 

![Cohort Retention Heatmap](executive_dashboard.png)

**Finding:** Early cohorts (May) show better retention than recent cohorts (June). Recent onboarding changes may have hurt activation.

**Recommendation:** A/B test onboarding versions. Roll back if new flow underperforms.

---

### 4. Revenue Impact Projection 

| Scenario | Current MRR | Projected MRR | Annual Impact |
|----------|------------|--------------|---------------|
| Current State | ₹95,000 | — | Baseline |
| +15% Activation Fix | ₹95,000 | ₹109,250 | **+₹1.7L/year** |
| +Channel Reallocation | ₹95,000 | ₹112,000 | **+₹2.0L/year** |
| Combined Optimizations | ₹95,000 | ₹125,000 | **+₹3.6L/year** |

---

## 🛠️ Technical Implementation

### Analytics Stack

| Layer | Tool | Purpose |
|-------|------|---------|
| **Data Collection** | Mixpanel JavaScript SDK | Event tracking, user identity |
| **Data Storage** | CSV / Event Warehouse | Raw event export |
| **Data Engineering** | Python + Pandas | Cleaning, transformation, feature engineering |
| **Analytics** | SQL-style queries (Python) | Cohort analysis, retention, funnel |
| **Visualization** | Matplotlib + Seaborn | Executive dashboards |
| **Statistical Analysis** | SciPy | Significance testing, correlation |

### Architecture

```
Raw Events (Mixpanel) → CSV Export → Python ETL → User Metrics → Cohort Analysis → Visualization → Insights
```

---

##  Data Model

### Event Taxonomy (snake_case)

| Event | Trigger | Properties |
|-------|---------|-----------|
| `user_signed_up` | Registration submitted | `channel`, `device`, `plan` |
| `onboarding_started` | Click "Start Onboarding" | `channel`, `device`, `plan` |
| `onboarding_completed` | All steps finished | `channel`, `device`, `plan`, `time_to_complete` |
| `feature_used` | Core feature interaction | `feature_name`, `channel`, `device`, `plan` |
| `subscription_upgraded` | Plan upgrade | `new_plan`, `upgrade_reason`, `previous_plan` |
| `user_churned` | 14+ days inactive | `churn_reason` |

### User Metrics Engine

```python
# Key metrics calculated per user
- signup_date
- started_onboarding (boolean)
- completed_onboarding (boolean)
- features_first_7 (count)
- activated (3+ features in week 1)
- upgraded (boolean)
- churned (boolean)
- time_to_onboard (hours)
```

---

## Results & Impact

### What I Built

✅ **3 Mixpanel Dashboards** — Acquisition, Activation, Retention  
✅ **Python Analytics Engine** — Cohort retention, channel ROI, statistical significance  
✅ **Executive Dashboard** — 6-chart visual summary for stakeholders  
✅ **Revenue Projections** — Data-backed financial impact of recommendations  

### Business Value

| Metric | Before | After (Projected) |
|--------|--------|-------------------|
| Onboarding Completion | 49.6% | 65% (+15%) |
| Day-7 Retention | ~6% | ~12% (2x) |
| LTV:CAC (Blended) | 1.8x | 3.2x (+78%) |
| Monthly Churn | 17% | 12% (-5pp) |
| MRR | ₹95K | ₹125K (+31%) |

---

## Files & Deliverables

| File | Description |
|------|-------------|
| `taskflow_events.csv` | 1,964 raw events (500 users, 6 event types) |
| `tracking_plan.md` | Event taxonomy, properties, KPI definitions |
| `analytics_engine.ipynb` | Full Python analysis (ETL → Insights) |
| `executive_dashboard.png` | 6-chart professional dashboard |
| `case_study.md` | Written analysis with recommendations |
| `linkedin_post.md` | Ready-to-publish content |
| `README.md` | This file |

---

## How to Run

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn scipy
```

### Quick Start

```python
import pandas as pd
from analytics_engine import GrowthAnalytics

# Load data
df = pd.read_csv('taskflow_events.csv')

# Initialize engine
engine = GrowthAnalytics(df)

# Run full analysis
engine.calculate_user_metrics()
engine.cohort_retention_analysis()
engine.channel_roi_analysis()
engine.generate_dashboard()

# Export results
engine.save_dashboard('my_dashboard.png')
```

### Mixpanel Integration

```javascript
// JavaScript SDK initialization
mixpanel.init('YOUR_PROJECT_TOKEN', {
  autocapture: true,
  persistence: 'localStorage'
});

// Track events
mixpanel.track('feature_used', {
  feature_name: 'create_task',
  channel: 'organic',
  plan: 'free'
});
```

---

##  What I Learned

1. **Funnel analysis is about finding leaks, not just measuring flow.** The 40% drop-off at onboarding Step 2→3 was invisible until I built the funnel.

2. **Not all users are equal.** Volume (Google Ads = 134 users) ≠ Value (Referral = 4.7x LTV:CAC). Quality metrics matter more than vanity metrics.

3. **Cohort analysis reveals trends hidden in averages.** Weekly retention curves showed early cohorts outperforming recent ones — signaling a product regression.

4. **Data without recommendations is just reporting.** The dashboard is useless without the "So what?" — I tied every insight to a specific action and projected revenue impact.

5. **Technical skills + business thinking = hireable analyst.** Python/SQL gets you the data. Business context gets you the job.

---

## Connect With Me

- **LinkedIn:** [https://www.linkedin.com/in/rahul-googikoll-121360275/]
- **Portfolio:** [https://rahulgoogikoll.com/]
- **Email:** [raulgoogikoll@gmail.com]

**Open to Data Analyst / Product Analytics roles.** Let's build something that matters.

---

## License

MIT License — feel free to use this as a template for your own analytics projects.

---

> *"Data doesn't just show what happened. It shows what to do next."*

**Built with 💙, Python, mixpanel and a lot of coffee.**
"""

with open('/mnt/agents/output/README.md', 'w') as f:
    f.write(readme_content)

print("README.md saved!")
print(f"\n Download: [README.md](sandbox:///mnt/agents/output/README.md)")
