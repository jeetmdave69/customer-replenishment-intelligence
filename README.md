# Customer Replenishment & Retention Intelligence System

## Overview
This project builds a rule-based customer replenishment intelligence engine using large-scale grocery transaction data.

The system models customer purchase rhythm, detects deviation from expected reorder cycles, and generates prioritized retention automation triggers.

## Business Objective
In repeat-purchase businesses (quick-commerce, grocery, food delivery), revenue depends heavily on timely reorders.
Customers deviating from their normal purchase rhythm represent churn risk.

This system identifies:

- Customers at risk of delayed reorder
- High-value customers requiring intervention
- Prioritized automation triggers for retention teams

## Dataset
Real-world grocery transaction dataset (200k+ customers, 3M+ orders).

Core tables used:
- orders.csv
- order_products__prior.csv
- products.csv

## Methodology

### 1. Customer Behavior Profiling
For each customer:
- Total orders
- Average reorder gap
- Reorder consistency (std deviation)

### 2. Stability Score
Predictability proxy:

stability_score = avg_reorder_gap / (reorder_gap_std + 1)

### 3. Overdue Detection
overdue_ratio = last_observed_gap / avg_reorder_gap

### 4. Risk Classification
- On Schedule
- Slightly Delayed
- At Risk
- High Risk

### 5. Priority Scoring
priority_score = stability_score × total_orders

## Key Insights
- Total Customers: 206,209
- High Risk Customers: 32,267 (15.65%)
- At Risk Customers: 35,573

## Output
Automated weekly retention trigger file:

reports/weekly_retention_triggers.csv

## Impact
This system enables:

- Data-driven retention automation
- Revenue protection through early churn detection
- Prioritized CRM intervention
- Scalable behavioral analytics without heavy ML
