---
author: Bear Jordan
date: Feb 19, 2025
paging: Slide %d / %d
---

# Optimizing Data Workflows
How Supplier-Facing Validation Saves Time and Headaches 

---

# Fundamental Problems in Data Engineering

1. Pressure from downstream consumers
2. No control over source data

---

# Key Take Aways

- Communication with source data owners is critical
- Don't just look at your database during optimization

---

# Background

## About Me

- Currently a data engineer at Relay Payments
- Previously worked at
  - Biden/Harris for President, Polling
  - Ministry of Statistics: New Zealand

---

# Background

## About Me

- Currently a data engineer at Relay Payments
- Previously worked at
  - **Biden/Harris for President, Polling** <- Focus of this talk
  - Ministry of Statistics: New Zealand

---

# Background

## The Problem

- **Stack**: GCP, Astro/Airflow, dbt
- **Work**: Daily reports for polling toplines to senior leadership.
- **Issues**:
  - Frequent back and forth with vendors over data quality delaying analysis
  - Each hour spent revising data is an hour not spent in analysis
- **Task**: Optimize our data pipeline so analysts have time to think 
- **Out of Talk's Scope**: Optimization within the data pipeline

---

# Investigation 

- **Ingestion**:
  - Vendors drop data into our bucket
  - Airflow + dbt processes the data
  - Analysts surface any dbt testing failures to vendors
  - If needed, vendors reupload data

- **Time Loss**:
  - Each iteration took between 30--90 min

---

# Solution

- Surface data quality checks to our data vendors

**Implementation**:
- Airflow polls our dropbox for new data
- When a new file is received, data is loaded into DuckDb
- Data quality tests were performed with SodaCL
- Results are templated into an email
- Email is sent to the vendor within 1 min

---

# Fundamental Problems in Data Engineering (Revisited)

1. Pressure from downstream consumers
  - Analysts had datasets available before they arrived to work
  - Eliminated context switching and communication delays for analysts
2. No control over source data
  - Data quality expectations were explicit increasing visibility
  - Vendors gained increase awareness about what data quality issues
    were common in their pipeline

**Optimization**: Didn't matter anymore

---

# Info

Shout Outs: HFP Polling/Eng, Jason Katz-Brown, and Steven Becerra

Conctact: [bearjordan@gmail.com]()

Slides: https://github.com/bear-jordan/pde-acceptance-testing
