# Metric Definitions

This page defines the standard KPI calculations used across the Task 3 dashboards to ensure consistent interpretation and calculation.

## Leadership Metrics

| Metric | Definition | Source |
|---|---|---|
| **Revenue** | Sum of `orders.total` for paid orders (`payment_status = 'paid'`). | `ecom.orders` |
| **Orders** | Count of distinct `order_id` for paid orders. | `ecom.orders` |
| **AOV** | Revenue ÷ distinct paid orders. | `ecom.orders` |
| **Conversion Rate** | Distinct sessions resulting in a paid order ÷ total distinct sessions × 100. | `ecom.sessions`, `ecom.orders` |
| **Refund Rate** | Distinct successfully refunded orders ÷ distinct paid orders × 100. | `ecom.refunds`, `ecom.orders` |
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

## Cross-Dashboard Consistency Check

**Metric:** Refund Rate

**Validation Period:** June 8, 2026 – June 14, 2026

### Definition

Distinct successfully refunded orders during the period  
÷  
Distinct paid orders during the period  
× 100

### Results

| Validation | Result |
|---|---:|
| Leadership Snapshot | **0.69%** |
| Ops/CX Dashboard | **0.7%** |
| Successfully Refunded Orders | **8** |
| Paid Orders | **1,162** |

### Manual Validation

```text
8 refunded orders ÷ 1,162 paid orders × 100
= 0.688468...
≈ 0.69%
```

**Result:** ✅ PASS

### Conclusion

Both dashboards use the same Refund Rate definition and the same 7-day comparison period.

The underlying Refund Rate is **0.69%**. The Leadership Dashboard displays **0.69%**, while the Ops/CX Dashboard displays **0.7%** because it is rounded to one decimal place.

The difference is display formatting only, not a metric-definition difference.