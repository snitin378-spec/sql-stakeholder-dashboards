# Leadership Snapshot — Product Requirements Document

## Dashboard Overview

**Dashboard Name:** Leadership Snapshot  
**User:** Founder / CEO  
**Database:** `ecom`  
**Refresh Cadence:** Daily  
**Primary Device:** Mobile and Desktop

## Purpose

The Leadership Snapshot dashboard provides the Founder/CEO with a quick overview of the company's business performance. It helps leadership monitor the most important KPIs every day, identify business issues early, and make informed decisions based on business performance.

## Job To Be Done

When the Founder/CEO reviews the dashboard each morning, they need to quickly understand the overall health of the business so they can identify problems early and make informed business decisions.

## Top 3 Decisions Enabled

1. Determine whether the business is performing better or worse compared to the previous week.
2. Identify any critical business issue that requires immediate attention, such as a sudden increase in refund rate or a drop in conversion rate.
3. Monitor whether the business is progressing toward its overall revenue and growth objectives.

## Stakeholder Interview

### Question 1
**What decision will you make after reviewing this dashboard each morning?**

First 30 seconds: Did yesterday break our revenue or CR trend compared to the same weekday last week? If revenue is down >15% WoW or refund rate spikes above 1.5%, I immediately ping Product or Ops before morning standup to find the leak. If KPIs are steady/green, I close the tab and let the teams execute without interruption.

### Question 2
**Which metric would be the most damaging if calculated incorrectly?**

Revenue and Conversion Rate. If Revenue is inflated (e.g. counting pending orders or failed retries), I make bad hiring and budget commitments. If Conversion Rate artificially reads 100% due to broken session denominators, Growth thinks campaigns are succeeding when users are actually bouncing.

### Question 3
**Who else will use this dashboard, and what information would they require?**

Board members and department heads (Growth, Ops, Finance) in our weekly sync. They need high-level weekly trends and channel/country contributions to align on company priorities, without getting bogged down in order-level operational noise.

## Metrics That Matter

### Hero KPIs

- Revenue with WoW %
- Orders with WoW %
- Average Order Value (AOV) with WoW %
- Conversion Rate with WoW %
- Refund Rate with WoW %

### Trend Analysis

- Daily Revenue — 90 Days with Prior Week Overlay
- Daily Paid Orders — Last 90 Days

### Breakdowns

- Revenue by Country — Top 5 with WoW
- Revenue by Acquisition Channel — Top 5 with WoW

### Diagnostic

- Leadership — 14-Day Diagnostic Table

## Required Filters

- Date Range — Default: Previous 30 days
- Country — Default: All
- Acquisition Channel — Default: All
- Payment Method — Default: All
- Device Type — Default: All

All dashboard filters are connected to the applicable Leadership dashboard cards.

## What's NOT in This Dashboard

### 1. Delivery and Courier Operational Metrics
**Reason:** Detailed delivery performance, courier SLA breaches, and fulfilment issues are operational metrics and are covered in the Ops/CX Dashboard.

### 2. Payment Failure Diagnostics
**Reason:** Payment-method and transaction-level failure analysis is intended for operational troubleshooting and is covered in the Ops/CX Dashboard.

### 3. Stuck Order Details
**Reason:** Individual orders requiring operational intervention do not belong in an executive-level business health dashboard. These are covered in the Ops/CX Dashboard.

### 4. Detailed Refund Reasons and Product Category Analysis
**Reason:** Leadership only needs Refund Rate as a high-level business health indicator. Detailed refund root-cause analysis is covered in the Ops/CX Dashboard.

## Information Hierarchy

1. **Hero KPIs** — immediate view of overall business health.
2. **Trend Charts** — identify changes and patterns over time.
3. **Country and Acquisition Channel Breakdowns** — identify the main drivers of business performance.
4. **Diagnostic Table** — supports deeper investigation when a KPI changes.

# Known Caveats 

- Conversion Rate and Payment Method: Payment Method is only available for sessions that progress to an order/payment attempt. Applying a Payment Method filter requires careful denominator handling so that Conversion Rate is not artificially inflated by excluding non-converting sessions. This is addressed separately in the Conversion Rate metric logic.
- WoW comparison: KPI Trend cards compare the latest reporting point with the corresponding point seven days earlier. The dashboard default reporting window is fixed to end on June 14, 2026 for consistent Task 3 evaluation.
- Acquisition attribution: Acquisition Channel analysis depends on the channel associated with the session and should be interpreted according to the available session-level attribution data.
- Executive scope: The dashboard intentionally excludes detailed operational diagnostics such as courier SLA issues, payment error codes, and individual stuck orders; these are handled in the Ops/CX Dashboard. 
- Conversion Rate denominator: The session denominator is calculated independently of Payment Method. Payment Method filters only the converted-session numerator, preventing non-converting sessions from being removed from the denominator. Validation: All methods = 16.32%; UPI = 4.66%.

## Wireframe

```text
Date Range | Country | Acquisition Channel | Payment Method | Device Type

--------------------------------------------------------------------------

Revenue | Orders | AOV | Conversion Rate | Refund Rate
  WoW      WoW     WoW        WoW              WoW

--------------------------------------------------------------------------

Daily Revenue — 90 Days with Prior Week Overlay

--------------------------------------------------------------------------

Daily Paid Orders — Last 90 Days

--------------------------------------------------------------------------

Revenue by Country              | Revenue by Acquisition Channel
Top 5 with WoW                  | Top 5 with WoW

--------------------------------------------------------------------------

Leadership — 14-Day Diagnostic Table

--------------------------------------------------------------------------

