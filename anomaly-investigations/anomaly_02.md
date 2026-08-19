# Anomaly Investigation 02 — Below-Target On-Time Delivery Performance

**Observation:** The Ops/CX dashboard shows an overall on-time delivery rate below the 90% target. To identify the source of the delivery issue, I analyzed delivery performance by region and courier.

**Hypotheses:** The below-target delivery performance could be broadly distributed across operations, or it could be concentrated within specific region and courier combinations.

**Tests:** I calculated delivered shipments, on-time shipments, late shipments, on-time percentage, and average late days by region and courier. Several EcomExpress region combinations showed on-time performance below 80%. Texas recorded 76.7% on-time delivery across 73 shipments, Delhi 79.7% across 311 shipments, Gujarat 79.8% across 287 shipments, and Uttar Pradesh 79.6% across 181 shipments.

I then compared performance at the overall carrier level. EcomExpress achieved **81.8% on-time delivery across 6,694 delivered shipments**, compared with **90.8% for Blue Dart across 6,667 shipments** and **93.8% for Delhivery across 6,682 shipments**. The carriers handled comparable shipment volumes, but EcomExpress underperformed both alternatives materially.

**Conclusion:** The delivery issue is primarily a **carrier-wide EcomExpress performance problem rather than an isolated regional issue**. The weak performance across multiple EcomExpress regions is consistent with its overall on-time delivery rate of 81.8%, which trails Blue Dart and Delhivery despite similar shipment volumes.

**So What:** Operations should prioritize a **carrier-level review with EcomExpress**, investigating capacity, routing, handoff processes, and SLA adherence across its network. The team should also evaluate whether shipment volume can be reallocated toward better-performing carriers such as Blue Dart or Delhivery while EcomExpress performance is addressed.