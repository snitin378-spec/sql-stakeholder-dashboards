# Anomaly Investigation 01 — Revenue Decline on June 14, 2026

**Observation:** On June 14, 2026, paid revenue fell to ₹421,219 from ₹1,951,822 on June 7, representing a 78.4% week-over-week decline. This was the most significant movement visible in the Leadership Snapshot.

**Hypotheses:** The decline could have been caused by lower traffic/session volume, lower conversion into paid orders, lower average order value (AOV), or incomplete data for June 14.

**Tests:** I compared June 14 with the same weekday one week earlier. Session volume declined from 1,007 to 429, a 57.4% decrease. Paid orders declined from 258 to 72, a 72.1% decrease, while AOV declined from ₹7,565 to ₹5,850, a 22.7% decrease. I also reviewed the hourly order profile. June 14 contained order activity across most hours of the day, including late-evening activity, indicating that the revenue decline was not caused by a simple partial-day data cutoff.

**Conclusion:** The revenue decline was primarily associated with substantially lower traffic and paid-order volume, with the decline in AOV providing an additional negative impact. Because paid orders fell more sharply than session volume, traffic reduction alone does not fully explain the anomaly; conversion performance should also be investigated. The hourly profile does not indicate a simple partial-day data issue.

**So What:** Leadership should investigate why traffic fell sharply on June 14 and why paid orders declined even faster than sessions. Acquisition/channel performance and conversion should be reviewed first, followed by the decline in AOV. The evidence supports treating June 14 as a genuine business-performance anomaly rather than dismissing it as a data-refresh issue.