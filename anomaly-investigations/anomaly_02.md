# Anomaly Investigation 02 — Below-Target On-Time Delivery Performance

## Observation

The Ops/CX dashboard shows an overall **On-Time Delivery Rate below the 90% target**.

To identify the source of the delivery issue, I analyzed delivery performance by region and courier.

## Hypotheses

The below-target delivery performance could be:

1. Broadly distributed across operations.
2. Concentrated within specific region and courier combinations.

## Tests

I calculated delivered shipments, on-time shipments, late shipments, on-time percentage, and average late days by region and courier.

Several **EcomExpress** combinations showed on-time performance below 80%.

| Region | On-Time Delivery % | Delivered Shipments | Late Shipments |
|---|---:|---:|---:|
| Texas | **76.7%** | 73 | 17 |
| Delhi | **79.7%** | 311 | 63 |
| Gujarat | **79.8%** | 287 | 58 |
| Uttar Pradesh | **79.6%** | 181 | 37 |

Texas recorded the lowest rate at **76.7%**, with 17 of 73 shipments late.

More importantly from a volume perspective, Delhi recorded **79.7%** on-time delivery across 311 shipments, including 63 late shipments. Gujarat recorded **79.8%** across 287 shipments, with 58 late shipments, while Uttar Pradesh recorded **79.6%** across 181 shipments, with 37 late shipments.

## Conclusion

The delivery issue is not simply an isolated low-volume anomaly.

Poor performance is visible across several **EcomExpress region combinations**, including high-volume regions such as Delhi and Gujarat.

## So What

Operations should prioritize EcomExpress performance in high-volume regions, especially **Delhi and Gujarat**, and investigate:

- Courier capacity
- Routing
- Handoff delays
- Regional fulfilment processes

Improving these high-volume combinations is likely to have greater impact on the overall On-Time Delivery KPI than focusing only on the lowest-performing small-volume region.