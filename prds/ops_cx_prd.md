# Ops/CX Dashboard — Product Requirements Document

## Dashboard Overview

**Dashboard Name:** Ops CX Dashboard  
**User:** Karthik — Head of Operations  
**Database:** `ecom`  
**Refresh Cadence:** Daily  
**Primary Device:** Desktop

## Purpose

The Ops CX Dashboard helps the Operations team monitor fulfilment, delivery performance, payment failures, refunds, and orders requiring intervention. It enables the team to identify operational issues quickly and take action before they result in increased customer complaints.

## Job To Be Done

When a courier in a particular region starts failing or a payment gateway begins generating errors, the Head of Operations needs to identify the issue quickly enough to escalate before customer complaints accumulate.

## Top 3 Decisions Enabled

1. Determine whether there is an operational issue that requires immediate escalation.
2. Identify whether delivery delays, payment failures, or refunds are deteriorating and determine where the problem is occurring.
3. Decide where operational improvements are required, such as courier performance, payment retry handling, or refund processes.

## Stakeholder Interview

### Question 1
**What operational decision will you make after reviewing this dashboard?**

**Answer:**  
[Paste the stakeholder's actual response here]

### Question 2
**Between On-Time Delivery %, Payment Failure Rate, and Refund Rate, which metric would be the most damaging if calculated incorrectly, and why?**

**Answer:**  
[Paste the stakeholder's actual response here]

### Question 3
**Who else will use this dashboard, and what information would they require?**

**Answer:**  
[Paste the stakeholder's actual response here]

## Metrics That Matter

### Hero KPIs

- On-Time Delivery % with WoW and threshold status
- Payment Failure Rate with WoW and threshold status
- Refund Rate with WoW and threshold status

### Fulfilment

- Order Status Funnel: Placed → Paid → Shipped → Delivered
- Average Time by Fulfilment Leg

### Delivery Operations

- On-Time Delivery % by Region and Courier
- Average Delay Days
- Number of Deliveries Delayed > 5 Days

### Payment Operations

- Payment Failure Rate by Payment Method
- Week-over-Week Payment Failure Trend by Method

### Refund Analysis

- Refund Rate by Product Category
- Top 5 Refund Reasons

### Actionable Operations

- Stuck Orders — Action Required

## What's NOT in This Dashboard

### 1. Revenue and AOV
**Reason:** Revenue and Average Order Value are leadership-level business performance metrics and are covered in the Leadership Snapshot Dashboard.

### 2. Acquisition Performance
**Reason:** Acquisition channel performance is primarily a Growth/Leadership concern and is not a direct operational lever for the Ops/CX team.

### 3. Product Feature Engagement
**Reason:** Product feature usage and engagement belong to Product Analytics and do not directly support operational incident management.

### 4. Detailed Executive Business Trends
**Reason:** Long-term revenue and overall business growth trends are covered in the Leadership Snapshot Dashboard. The Ops/CX Dashboard focuses on operational problems that require investigation or action.

## Information Hierarchy

1. **Hero KPIs** — quickly identify whether an operational problem exists.
2. **Fulfilment Analysis** — identify where orders are slowing down between Placed, Paid, Shipped, and Delivered.
3. **Delivery, Payment, and Refund Breakdowns** — identify the region, courier, payment method, or product category driving the issue.
4. **Actionable Stuck Orders List** — identify the exact orders requiring operational intervention.

## Known Caveats
- Reporting window: The dashboard default reporting range is fixed to end on June 14, 2026 for consistent Task 3 evaluation. KPI Trend cards compare the latest 7-day reporting period with the preceding 7-day period.
- Delivery SLA: On-Time Delivery uses a fixed 5-day SLA from shipped_at to delivered_at; differences in courier- or region-specific contractual SLAs are not modeled.
- Payment failures: Payment Failure Rate is calculated from recorded payment transactions. It reflects transaction failures and does not independently identify the root cause of a gateway failure.
- Stuck orders: Stuck-order identification is based on the defined age/status rule and should be treated as an operational investigation queue rather than proof that every listed order requires the same intervention.
- Region/Courier comparisons: Low-volume region/courier combinations can produce volatile percentages; volume should be considered alongside On-Time Delivery % when prioritizing operational action.

## Wireframe

```text
                         OPS / CX DASHBOARD

--------------------------------------------------------------------------

On-Time Delivery % | Payment Failure Rate | Refund Rate
WoW / Status         WoW / Status           WoW / Status

--------------------------------------------------------------------------

Order Status Funnel | Average Time by Fulfilment Leg

--------------------------------------------------------------------------

Delivery Performance by Region and Courier

--------------------------------------------------------------------------

Payment Failure Rate by Method — Weekly Trend

--------------------------------------------------------------------------

Refund Rate by Product Category | Top 5 Refund Reasons

--------------------------------------------------------------------------

Stuck Orders — Action Required

Order | Status | Payment Status | Location | Days Open

--------------------------------------------------------------------------
```