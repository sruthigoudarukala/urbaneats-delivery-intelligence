# UrbanEats Delivery Operations Intelligence

End-to-end data pipeline that identifies cancellation hotspots, scores orders by risk, and automates daily ops briefings for regional managers.

## Problem
UrbanEats saw a 22% rise in cancellations and delivery complaints over one quarter. No one knew which restaurants, zones, or riders were causing the breakdown.

## What I Built

### Part A — Data Profiling
- Profiled 150 orders using ydata-profiling
- Found 6 orders missing `delivery_time_mins` concentrated in Cancelled/Delayed orders
- Identified this as the field most likely to distort delivery time analysis

### Part B — Data Quality Gate
- Implemented 6 Great Expectations checks: order ID uniqueness, delivery time range, rider rating range, valid order statuses, order value bounds
- All 6 expectations passed — dataset cleared for analysis

### Part C — Cancellation Risk Classifier + AI Alerts
- Trained a Random Forest classifier on Delivered vs Cancelled orders
- Top cancellation drivers: delivery time (27%), order value (20%), discount applied (18%)
- **Highest risk hotspot: Spice Garden — Central zone**
- Scored all 150 orders with `cancel_probability` and `cancel_risk` columns
- Generated ops alerts using LangChain + Claude API for restaurant-zone pairs with >30% high cancel risk

### Part D — Automated Morning Briefing (n8n)
- 8-node n8n workflow firing at 07:30 daily
- Fetches scored CSV → computes metrics → branches on cancellation rate threshold
- Red alert (>20% cancellation rate) → Slack #ops-alerts + Gmail
- Green summary (within threshold) → Slack #ops-alerts + Gmail

## Key Finding
Spice Garden in the Central zone carries the highest cancellation risk, driven by long delivery times and
