# RideIT Driver & Ride Performance Dashboard

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## Overview

A Power BI analytics dashboard built to monitor and analyze driver performance, bookings, ride engagement, cancellations, and service-type trends for the RideIT mobility platform. This repository contains the Power BI report (`.pbix`), supporting images, and documentation to help data teams and business stakeholders reproduce and extend the analysis.

---

## Key Highlights & Analysis Report

### 📌 Full Analytical Summary

#### **1. Driver Performance Overview (Page 1)**

The platform has **37K registered and active drivers**, showing a stable and consistent workforce. Activity levels fluctuate across months:

* **January–February** show strong driver participation.
* **April** marks the lowest activity, indicating an operational or seasonal impact.
* Gradual recovery during **May–June**.

**Country-wise insights:**

* **Denmark** leads driver supply with **1.28M activity count**, significantly higher than Spain.

**Service Type Split:**

* TAXI drivers dominate the fleet with **~85% share**, while PHV contributes **15%**.

**Marketing Impact:**

* Drivers acquired through marketing campaigns represent a major portion (**1.39M**) compared to non-marketing drivers (**0.44M**).

---

#### **2. Marketplace & Ride Experience Analytics (Page 2)**

**Ride Completion Rate:** Healthy at **82%**, showing reliable driver operations.

**Acceptance Rate:** **28%**, suggesting:

* Drivers might be selective.
* Possibly high “offer-to-booking” ratio.
  This indicates a need to optimize offer distribution and driver incentives.

**Cancellation Analysis:**

* Passenger cancellations (e.g., 0.43M for TAXI) are higher than driver cancellations.
* This may relate to long wait times, pricing issues, or rider uncertainty.

**Marketing Contribution:**

* Marketing campaigns generate **21M offers**, **6M bookings**, and **5M rides**.
* Non-marketing users generate significantly less activity.

**Trend Analysis (Jan–Jun 2020):**

* Acceptance rate improved until **April**, then slightly stabilized.
* Cancellation rate had minor fluctuations but stayed below **0.3–0.4**, indicating good operational control.

---

#### **3. Operational Deep-Dive & Driver Tenure Performance (Page 3)**

**Day-wise analysis:**

* **Saturday** and **Wednesday** have the highest volumes of offers and bookings.
* **Monday** shows the lowest overall marketplace movement.

**Driver tenure segmentation:**

* **New Drivers** (17K+) contribute the most bookings, rides, and cancellations.
* **Senior Drivers** show the highest consistency in ride completion and lowest cancellations.
* **Experienced Drivers** hold the best average ratings (**~4.88–4.89**).

**Cancellation Behavior:**

* New drivers show relatively higher driver cancellations (326K), indicating a need for:

  * Better onboarding
  * Training
  * Incentive realignment

**Customer cancellations** peak on days with high offer volumes, indicating possible demand-supply mismatch.

---

### 📌 Summary of Insights

* Denmark is the key driver hub.
* TAXI accounts for the majority of the platform's supply and demand.
* Marketing significantly boosts engagement and transactions.
* Passenger cancellations exceed driver cancellations.
* New drivers require operational support due to high cancellation volumes.
* April dips across metrics hint at external/systemic challenges.
* Strong weekend performance, especially Saturdays.

---

* Visualize driver activity and trends (monthly and by country)
* Track marketplace KPIs: total offers, bookings, rides, completion and acceptance rates
* Cancellation analysis broken down by `cancelled_by` (customer vs driver)
* Compare service types: `TAXI` vs `PHV` (Private Hire Vehicle)
* Measure marketing impact on offers, bookings and rides
* Interactive filtering by date range, country, service type, and marketing flag

---

## Screenshots

Page 1 — Driver Performance Overview
![Driver Overview](https://github.com/manasa-dumpala2003/RideIT-Data-Analysis-Dashboard/blob/main/rideit1.png)

Page 2 — Operational & Marketplace Analytics
![Marketplace Analytics](https://github.com/manasa-dumpala2003/RideIT-Data-Analysis-Dashboard/blob/main/rideit2.png)

Page 3 — Aggregated Metrics & Tenure Table
![Tenure & Day-of-week Analysis](https://github.com/manasa-dumpala2003/RideIT-Data-Analysis-Dashboard/blob/main/rideit3.png)

---


## Dataset (example schema)

The dashboard was created from an aggregated rides/bookings dataset. Example columns used:

```
booking_id
ride_status
driver_id
booking_datetime
country_code
service_type       # TAXI | PHV
is_marketing       # True | False
cancelled_by       # customer | driver | NULL
accepted_flag
offers_count
```

The dataset contained activity from **Jan 2020 — Jun 2020** for Denmark and Spain in the sample visuals.

---

## DAX / Key Measures (examples)

```DAX
Total Bookings = COUNTROWS(Bookings)
Total Rides = CALCULATE(COUNTROWS(Bookings), Bookings[ride_status] = "completed")
Ride Completion Rate = DIVIDE([Total Rides], [Total Bookings], 0)
Acceptance Rate = DIVIDE([Accepted Bookings], [Total Bookings], 0)
Driver Cancellation Rate = DIVIDE([Driver Cancellations], [Total Bookings], 0)
```

Include additional measures for marketing-attributed metrics and segmented aggregation by `service_type`, `country_code`, and `driver_tenure`.

---


## Recommended Enhancements

* Add supply-demand heatmap (geo/spatial visual)
* Driver incentive optimization model (DAX + R/Python integration)
* Predictive driver churn model using feature store and scheduled refresh
* Add parameterized report templates and documentation for dataset mapping



