# Analysis Notes & Design Decisions  
Operational Backlog Monitoring & Risk Analysis (Excel)

---

## 1. Project Context & Scope

This project was designed to simulate a **real-world operational analytics assignment**, using a large, messy public dataset and building a reporting system entirely in Excel.

The goal was **not** to extract a single domain insight from NYC 311 data, but to demonstrate the ability to:

- Work with high-volume, time-based operational data
- Clean and model data for analysis in Excel
- Design stable, explainable metrics
- Build multi-page reports that answer distinct business questions
- Communicate findings clearly to different stakeholders

Excel was intentionally chosen as the only tool to reflect environments where BI tools may not be available and where analysts are expected to deliver insight using spreadsheet-based workflows.

---

## 2. Metric Definitions & Logic

This section documents how key analytical fields and metrics were defined.

### Request Status
- **Open Request (`is_open = 1`)**  
  A request with no valid closed date.
- **Closed Request (`is_closed = 1`)**  
  A request with a valid closed date.

These flags were created in Power Query to ensure consistent logic across all analyses.

---

### Resolution Time
- **Resolution Time (Days)**  
  Calculated as the difference between `Closed Date` and `Created Date`.
- Requests without a closed date do not contribute to resolution-time metrics.

Resolution time is used only for **closed requests** to avoid misleading calculations.

---

### Aging Buckets (Open Requests Only)

Open requests were grouped into aging buckets to assess backlog risk:

- 0–7 days  
- 8–30 days  
- 31–90 days  
- 91–180 days  
- 181–365 days  
- 1–2 years  
- 2+ years  

These buckets were designed to reflect increasing operational risk and neglect over time.

---

### Long-Delay Definition

- **Long Delay**  
  A closed request with a resolution time greater than **90 days**.
- A binary flag (`is_long_delay`) was created:
  - `1` → resolution time > 90 days  
  - `0` → otherwise

This flag enables clear identification of extreme delays without relying on unstable percentile calculations.

---

## 3. Design Decisions & Trade-offs

Several intentional design decisions were made during this project.

### Removal of Median and Percentile Metrics
Median and percentile-based metrics were initially considered but ultimately **removed** because:

- Excel PivotTables handle medians unreliably with slicers
- Percentile calculations are inconsistent across Excel versions
- These metrics often broke or became static under filtering

Instead, the analysis uses:
- **Average Resolution Time**
- **Long-Delay Count**
- **Long-Delay Rate**

These metrics are stable, slicer-safe, and operationally meaningful.

---

### Column Reduction
Many columns in the original dataset were removed due to:
- Extremely high null rates
- Lack of analytical relevance
- No contribution to backlog, demand, or performance analysis

Only columns required for operational insight were retained.

---

### Page-Level Design Choices
Each report page was designed to answer **one core business question**:

- Page 1: Overall system health
- Page 2: Demand and inflow patterns
- Page 3: Resolution efficiency and delay risk
- Page 4: Backlog aging and ownership risk

Page 4 was intentionally simplified to focus on a **single risk-concentration visual**, rather than multiple overlapping charts.

---

## 4. Known Data Limitations

The analysis acknowledges the following limitations:

- Older historical records inflate average resolution times
- Some early records lack reliable closed dates
- Agencies with low request volumes may show exaggerated rates
- Open requests may still be legitimately pending, not neglected

These limitations were considered during interpretation and documented to avoid misleading conclusions.

---

## 5. Intended Real-World Usage

If deployed in a real organization:

- **Executives** would use Page 1 for system-level monitoring
- **Operations managers** would focus on Pages 3 and 4
- **Analysts** could drill into Page 2 for demand pattern analysis
- Page 4 would guide prioritization of backlog reduction efforts

With additional data (SLAs, staffing levels, escalation rules), the system could be extended into predictive or capacity-planning analysis.

---

## 6. Summary

This project emphasizes analytical judgment over technical tricks.  
The focus was on building a **stable, explainable, and decision-oriented Excel reporting system**, supported by clear documentation of assumptions and trade-offs.

---
