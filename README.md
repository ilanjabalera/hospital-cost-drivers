# Hospital Cost Drivers & High-Cost Cohort Analysis

## Overview
Hospital costs are often highly concentrated within a relatively small subset of patients.  
This project analyzes hospital encounter data to identify **which encounters drive the majority of total charges**, **what factors explain these costs**, and **which patient cohorts should be prioritized for intervention**.

The analysis is designed from a **healthcare operations and decision-making perspective**, with SQL as the primary analytical tool.

---

## Problem Statement
Healthcare systems frequently struggle with rising costs without clear visibility into:
- Which encounters account for most of the spending
- What clinical and operational factors drive these costs
- Where targeted interventions could yield the greatest impact

Understanding cost concentration and its drivers is critical for effective resource allocation.

---

## Data
This project uses a **simulated hospital encounters dataset** designed to reflect realistic healthcare utilization patterns.

Each row represents a hospital encounter with variables including:
- Age and sex
- Payer type (Medicare, Medicaid, Private, Self-pay)
- Admission type (Emergency, Elective, Urgent)
- Length of stay
- Diagnosis group
- Total hospital charges

The dataset was intentionally simulated to allow full reproducibility while preserving realistic cost distributions and outliers commonly observed in hospital data.

---

## Methodology
The analysis follows a structured approach:

1. **Data Preparation**
   - Generated and cleaned encounter-level data
   - Stored the dataset as a CSV for reproducibility

2. **SQL-Based Analytics**
   - Loaded data into DuckDB
   - Performed all major analyses using SQL queries
   - Used window functions for Pareto analysis

3. **Pareto Analysis**
   - Identified the share of encounters responsible for the majority of total charges

4. **Cost Driver Analysis**
   - Analyzed total, average, and median charges by:
     - Diagnosis group
     - Admission type
     - Payer
     - Length of stay buckets

5. **High-Cost Cohort Identification**
   - Defined high-cost encounters as the top ~30% of total charges
   - Identified recurring combinations of clinical and operational factors

---

## Key Findings
- Approximately **31% of hospital encounters account for nearly 60% of total charges**, indicating significant cost concentration.
- Emergency admissions contribute disproportionately to total hospital costs.
- Neurology, cardiology, pulmonology, and endocrinology consistently rank among the highest-cost diagnosis groups.
- Medicare encounters dominate high-cost cohorts, particularly in emergency settings.
- Length of stay shows a strong nonlinear relationship with cost, with encounters exceeding 3–5 days driving a large share of total charges.
- High-cost encounters cluster around specific combinations of diagnosis, admission type, payer, and length of stay rather than occurring randomly.

---

## Actionable Insights
The findings suggest several opportunities for targeted intervention:
- Prioritize care coordination for emergency Medicare patients with high-risk diagnoses.
- Implement early discharge planning for encounters likely to exceed 3–5 days of stay.
- Focus case management and follow-up resources on identified high-cost cohorts.
- Use cohort-based strategies rather than broad, uniform cost-reduction initiatives.

---

## Project Structure

#hospital-cost-drivers/
├── data/
│ ├── raw/
│ └── processed/
├── notebooks/
│ └── 01_build_dataset.ipynb
├── reports/
│ ├── tables/
│ └── figures/
├── sql/
├── src/
├── health.db
└── README.md

## Tools & Technologies
- Python
- DuckDB
- SQL
- Pandas
- Jupyter Notebook

---

## Notes
This project emphasizes **clarity, interpretability, and decision relevance** over model complexity.  
Machine learning is intentionally treated as optional, with the primary focus placed on explainable, SQL-driven analysis aligned with real-world healthcare operations.
