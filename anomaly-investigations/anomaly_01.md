# Anomaly Investigation 01 — Revenue Decline on June 14, 2026

## Observation

On June 14, 2026, paid revenue fell to **₹421,219** from **₹1,951,822** on June 7, representing a **78.4% week-over-week decline**.

This was the most significant movement visible in the Leadership Snapshot.

## Hypotheses

The decline could have been caused by:

1. Lower paid-order volume.
2. Lower Average Order Value (AOV).
3. Incomplete data for June 14.

## Tests

I compared June 14 with the same weekday one week earlier.

| Metric | June 7, 2026 | June 14, 2026 | Change |
|---|---:|---:|---:|
| Paid Revenue | ₹1,951,822 | ₹421,219 | **-78.4%** |
| Paid Orders | 258 | 72 | **-72.1%** |
| AOV | ₹7,565 | ₹5,850 | **-22.7%** |

I then checked data completeness.

Orders were recorded from **12:15 AM through 11:28 PM on June 14**, confirming that the date represents a full day rather than a partial data load.

## Conclusion

The revenue decline was driven by both lower paid-order volume and lower AOV, with the substantial reduction in order volume being the primary driver.

The completeness test did not indicate a partial-day data issue.

## So What

Leadership should prioritize investigating the reason for the sharp reduction in paid orders on June 14, including **acquisition/channel and conversion performance**, while also reviewing the decline in AOV.

This should be treated as a **business-performance anomaly rather than dismissed as a data-refresh issue**.