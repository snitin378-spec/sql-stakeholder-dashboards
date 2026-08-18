# Metric Definitions

This page defines the standard KPI calculations used across the Task 3 dashboards to ensure consistent interpretation and calculation.

## Leadership Metrics

| Metric | Definition | Source |
|---|---|---|
| **Revenue** | Sum of `orders.total` for paid orders (`payment_status = 'paid'`). | `ecom.orders` |
| **Orders** | Count of distinct `order_id` for paid orders. | `ecom.orders` |
| **AOV** | Revenue ÷ distinct paid orders. | `ecom.orders` |
| **Conversion Rate** | Distinct sessions resulting in a paid order ÷ total distinct sessions × 100. | `ecom.sessions`, `ecom.orders` |
| **Refund Rate** | Distinct successfully refunded paid orders created during the reporting period ÷ distinct paid orders created during the reporting period × 100. | `ecom.refunds`, `ecom.orders` |
| **WoW %** | `(Current value − Previous week value) ÷ Previous week value × 100`. | Derived |

## Ops/CX Metrics

| Metric | Definition | Source |
|---|---|---|
| **On-Time Delivery %** | Delivered shipments completed within 5 days of `shipped_at` ÷ total delivered shipments × 100. | `ecom.shipments` |
| **Payment Failure Rate** | Failed payment transactions ÷ total payment transactions × 100. | `ecom.payment_transactions` |
| **Refund Rate** | Distinct successfully refunded orders ÷ distinct paid orders × 100. | `ecom.refunds`, `ecom.orders` |
| **Average Order-to-Ship Time** | Average elapsed hours between `orders.created_at` and `shipments.shipped_at`. | `ecom.orders`, `ecom.shipments` |
| **Average Ship-to-Delivery Time** | Average elapsed hours between `shipments.shipped_at` and `shipments.delivered_at`. | `ecom.shipments` |
| **Average Delay Days** | Average number of days delivered shipments exceeded the 5-day SLA; non-delayed shipments contribute 0 days. | `ecom.shipments` |
| **Delayed > 5 Days** | Count of delivered shipments where `delivered_at > shipped_at + 5 days`. | `ecom.shipments` |
| **Stuck Orders** | Orders in a non-terminal status for more than 2 days relative to the dataset's latest order date. | `ecom.orders` |
| **Refund Rate by Product Category** | Distinct successfully refunded orders associated with a category ÷ distinct paid orders associated with that category × 100. | `ecom.refunds`, `ecom.order_items`, `ecom.product_variants`, `ecom.products`, `ecom.categories`, `ecom.orders` |

# Cross-Dashboard Consistency Check

**Metric:** Refund Rate

**Canonical Definition:**

Distinct successfully refunded paid orders created during the reporting period  
÷  
Distinct paid orders created during the reporting period  
× 100.

## Multi-Window Validation

| Validation Window | Leadership Snapshot | Ops/CX Dashboard | Result |
|---|---:|---:|---|
| Apr 1–30, 2026 | 0.57% | 0.6% | PASS |
| May 16–Jun 14, 2026 | 0.52% | 0.5% | PASS |
| Jun 1–7, 2026 | 0.61% | 0.6% | PASS |

**Result:** PASS

The metric was tested across multiple reporting windows to confirm that both dashboards respond dynamically to the Date Range filter and use the same canonical Refund Rate definition.

The small displayed differences are due only to formatting: the Leadership Snapshot displays Refund Rate to two decimal places, while the Ops/CX Dashboard displays it to one decimal place.