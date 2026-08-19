# Anomaly Investigation 01 — Revenue Decline on June 14, 2026

**Observation:** On June 14, 2026, paid revenue fell to ₹421,219 from ₹1,951,822 on June 7, representing a 78.4% week-over-week decline.

**Hypotheses:** The decline could have been caused by lower order volume, lower AOV, a genuine demand decline, or incomplete/under-populated data at the dataset boundary.

**Tests:** I compared June 14 with the same weekday one week earlier. Paid orders declined from 258 to 72, a 72.1% decrease, while AOV declined from ₹7,565 to ₹5,850, a 22.7% decrease.

I then tested data completeness beyond simply checking the first and last order timestamps. June 14 recorded **429 sessions compared with 1,007 sessions on June 7**. Activity was lower across all 24 hours, with the median hourly session volume at approximately **40% of June 7's level** and no distinct intraday cutoff point.

**Conclusion:** Although June 14 contains activity throughout the full day, the uniformly lower hourly session volume indicates that the final dataset date is likely **under-populated**. Therefore, the apparent 78.4% revenue decline should not be treated as a confirmed business-performance deterioration.

**So What:** Leadership should avoid escalating the June 14 revenue decline as a business anomaly until data completeness is confirmed. For anomaly investigations, the final date of a dataset should be treated cautiously, and hourly traffic/session-volume checks should be used alongside timestamp coverage before drawing business conclusions.