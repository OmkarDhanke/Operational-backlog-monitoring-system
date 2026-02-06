# 📊 Operational Backlog Monitoring & Risk Analysis (Excel)

## 🧭 Project Overview
This project demonstrates how a large, real-world operational dataset can be transformed into a **decision-ready Excel reporting system** using structured data modeling, Power Query, PivotTables, and multi-page dashboards.

The focus is **not a single domain insight**, but the ability to:
- clean and model messy operational data,
- design stable and explainable metrics,
- analyze demand, performance, and backlog risk,
- communicate insights through a professional Excel report.

The final output is a **four-page, fully navigable Excel report**, built entirely in Excel without external BI tools.

---

## Dataset
- **Source:** NYC 311 Service Requests (2010–2024)
- **Size:** 100,000+ records
- **Type:** High-volume, time-based operational request data

### Key Data Challenges
- Missing and inconsistent date fields  
- Extremely skewed resolution times  
- Large number of irrelevant or sparsely populated columns  
- Long historical range requiring careful time anchoring  

---

## 🎯 Project Objectives
- Build a **stable analytical foundation** in Excel (no fragile formulas)
- Track operational backlog and resolution performance over time
- Identify demand drivers, efficiency gaps, and backlog risk
- Design a reporting structure similar to what real operations or analytics teams use

---

## Tools & Techniques Used
- **Microsoft Excel**
  - Power Query for data cleaning and feature engineering
  - PivotTables for scalable analysis
  - Slicers for cross-page interactivity
  - Custom chart layouts and navigation
- **Git & GitHub**
  - Industry-style repository structure
  - Incremental commits documenting project progress

> No external BI or visualization tools were used.

---

## 🧩 Data Preparation & Modeling
All transformations were performed in **Power Query**, including:

- Standardizing and validating date fields  
- Removing unused and near-empty columns  
- Creating analytical flags and derived fields:
  - `is_open`, `is_closed`
  - `resolution_time_days`
  - `aging_bucket`
  - `is_long_delay` (90+ days)
- Ensuring all metrics are **slicer-safe and stable**

Median and percentile-based metrics were intentionally avoided due to Excel limitations and replaced with more robust operational indicators.

---

## 📈 Report Structure & Dashboard Walkthrough

### 🔹 Page 1: Operational Overview & Control Panel
**Purpose:** Executive snapshot of the current operational state  

![Page 1 – Overview](outputs\OperationalOverview.png)

**What this page answers:**
- How many requests exist overall?
- How much of the backlog is still open?
- How healthy is resolution performance at a high level?

**Key elements:**
- Total requests, open requests, closed requests
- Open backlog percentage
- Average resolution time
- Creation vs closure trend
- Net backlog change
- High-level backlog aging
- Central navigation and global slicers

This page functions as the **control panel** for the entire report.

---

### 🔹 Page 2: Request Volume & Demand Analysis
**Purpose:** Understand request inflow patterns and demand composition  

![Page 2 – Volume & Demand](.\outputs\RequestVolume.png)

**What this page answers:**
- How does request volume change over time?
- What types of requests drive the most demand?
- Is demand composition shifting?

**Key analysis:**
- Monthly request volume trend
- Top request categories by volume
- Demand mix evolution over time

This page focuses on **what is coming into the system**.

---

### 🔹 Page 3: Resolution Performance Analysis
**Purpose:** Evaluate efficiency and identify performance risk  

![Page 3 – Resolution Performance](\outputs\ResolutionPerformance.png)

**What this page answers:**
- How long do requests typically take to resolve?
- Which agencies are slower or faster?
- Where are extreme delays concentrated?

**Key analysis:**
- Distribution of resolution time
- Average resolution time by agency
- Exposure to long-delay resolutions (90+ days)
- Long-delay rate by agency

This page focuses on **how well work is being resolved**, not just how much work exists.

---

### 🔹 Page 4: Backlog Risk & Aging Analysis
**Purpose:** Highlight operational risk and ownership  

![Page 4 – Backlog Risk](\outputs\BacklogRisk.png)

**What this page answers:**
- Where is the open backlog aging?
- Which agencies own the highest-risk backlog?
- Where should immediate attention be applied?

**Key analysis:**
- Open backlog by aging category
- Agencies with the highest long-pending backlog
- Severity breakdown of open backlog
- Open backlog risk concentration by agency

This page **closes the story** by clearly identifying where action is required.

---

## 🧠 Design Principles Followed
- Clear separation between:
  - data layer
  - metric layer
  - analysis layer
  - reporting layer
- No duplicated or misleading metrics
- Each report page answers a **specific business question**
- Visual variety without unnecessary complexity
- Built for explanation, not decoration

---

## ✅ Key Takeaways
- Large operational datasets require **careful modeling**, not just visuals
- Stable metrics matter more than complex ones in Excel
- A well-structured Excel report can support decision-making as effectively as BI tools when designed correctly

---

* **Author:** **Omkar Dhanke**    
* **Connect with me:** [![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/omkar-dhanke)
