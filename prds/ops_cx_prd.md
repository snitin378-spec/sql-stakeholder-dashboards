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

Every morning at 9 AM: Check On-Time Delivery and Payment Failure Rate. If a carrier drops below 85% on-time delivery in high-volume regions or payment failure spikes above 5%, I immediately re-allocate warehouse shipments to backup carriers (Blue Dart/Delhivery) or escalate gateway errors to engineering. Then I triage the Stuck Orders queue (>48h unfulfilled) to clear high-value blockers.

### Question 2
**Between On-Time Delivery %, Payment Failure Rate, and Refund Rate, which metric would be the most damaging if calculated incorrectly, and why?**

Payment Failure Rate in real-time — if a gateway outage or 75% UPI failure goes undetected for 4 hours, customers abandon their carts permanently and that revenue is lost forever. On-Time Delivery is second because courier SLA breaches trigger CX ticket floods and chargebacks.

### Question 3
**Who else will use this dashboard, and what information would they require?**

Warehouse fulfillment leads, Courier Partner Account Managers, and CX escalation leads. Warehouse leads need the Stuck Orders queue (>48h paid, unfulfilled) and zero-inventory stockouts; Courier managers need volume and SLA breach counts by courier/region to hold carriers accountable in weekly reviews.

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

### Inventory Health

- Stockouts — Action Required: Product/SKU combinations where current on-hand inventory equals zero.
- Inventory Shrink Rate — Daily: Percentage of outbound inventory units associated with adjustment_negative, damage, or theft.

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
- Stuck orders: The operational queue identifies paid orders with no shipment record more than 48 hours after order creation. Results are prioritized by order value so higher-value orders requiring fulfilment intervention appear first.
- Region/Courier comparisons: Low-volume region/courier combinations can produce volatile percentages; volume should be considered alongside On-Time Delivery % when prioritizing operational action.
- Inventory shrink: Shrink Rate is defined as outbound units associated with adjustment_negative, damage, or theft divided by total outbound inventory units. This is an operational monitoring definition based on the available inventory movement reasons and is not intended as a formal accounting shrink measure.

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
Stockouts — Action Required | Inventory Shrink Rate — Daily