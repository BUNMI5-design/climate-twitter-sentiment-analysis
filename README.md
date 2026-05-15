# 🌍 Climate Change Twitter Sentiment Analysis
### End-to-End Data Analytics Project | PostgreSQL + Power BI

![Project Banner](https://img.shields.io/badge/Status-Completed-brightgreen)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15-blue)
![PowerBI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow)
![Rows](https://img.shields.io/badge/Dataset-15.7M%20Rows-orange)
![HNG](https://img.shields.io/badge/HNG%2014-Stage%204%20%7C%203rd%20Place-gold)

---

## 📌 Project Overview

As a contracted **Senior Data Analyst** for a climate research organisation, I independently managed a full end-to-end data analytics pipeline — from raw data ingestion to a published interactive dashboard — on one of the largest publicly available Twitter datasets in existence.

The objective was to help leadership understand **how global public sentiment and stance on climate change have shifted over 14 years**, and which topics and regions are driving the most divisive or aggressive discourse — ahead of a major policy briefing.

> 🏆 **Achievement:** Ranked **3rd out of all participants** in HNG 14 Data Analytics Stage 4 with a score of **8.68/10**

---

## 📊 Live Dashboard

🔗 **[View Interactive Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNTgxMWVlNDMtZTQ0NS00ODhmLTg4NGEtZjZlZWQ1ZjhjMTdkIiwidCI6Ijg4MTM1NDc1LTU1NzctNGVjZC04NDAyLWU0NDRiM2FmMDJjNiIsImMiOjZ9)**

📁 **[View Full Project Files on Google Drive](https://drive.google.com/drive/folders/1NKokdEK290k804Hn6oAhWmFNoUOdUZTe?usp=sharing)**

---

## 🗂️ Dataset

| Detail | Value |
|---|---|
| **Source** | The Climate Change Twitter Dataset — Mendeley Data v2 |
| **Citation** | DOI: 10.1016/j.eswa.2022.117541 |
| **Main Table** | 15,789,411 tweets (2006–2019) |
| **Companion Table** | 4,913 climate disaster events across 203 countries |
| **Columns** | created_at, tweet_id, lng, lat, topic, sentiment, stance, gender, temperature_avg, aggressiveness |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **PostgreSQL 15** | Data storage, cleaning, transformation, and all analytical queries |
| **Power BI Desktop** | Interactive dashboard and data visualisation |
| **pgAdmin 4** | PostgreSQL GUI and query execution |
| **SQL** | 29 analytical queries across descriptive and diagnostic analytics |

---

## 📁 Repository Structure

```
climate-twitter-analysis/
│
├── Climate_Analysis.sql        # Complete SQL file — all queries and views
├── Analyst_Report.pdf          # Full analytical report (PDF)
├── Analyst_Report.docx         # Full analytical report (Word)
└── README.md                   # Project documentation
```

---

## 🔍 What I Did

### 1. Data Loading & Ingestion
- Loaded 15,789,411 tweets into PostgreSQL using `\copy` command
- Loaded 4,913 disaster events from companion dataset
- Verified row counts and data integrity post-load

### 2. Data Cleaning & Preparation
- Identified and handled 10,481,873 missing coordinates (66.4%) — retained with `has_geolocation` flag
- Fixed topic name typo: `Intervantion` → `Intervention`
- Standardised categorical values (stance, gender, aggressiveness) to Title Case
- Validated sentiment scores — zero out-of-range values found
- Zero duplicates found across 15.7M records
- Performed statistical outlier check on temperature deviation (range: -23.29°C to +21.00°C — clean)
- Created `tweets_clean` table with 20+ derived columns

### 3. Data Transformation (15 SQL Views)
Created 15 pre-aggregated PostgreSQL views for Power BI connection:

| View | Purpose |
|---|---|
| `vw_tweets_master` | Full cleaned dataset for slicer-driven filtering |
| `vw_yearly_trends` | KPIs and trends by year |
| `vw_topic_analysis` | Topic-level sentiment and aggressiveness metrics |
| `vw_regional_analysis` | Continent-level discourse analysis |
| `vw_stance_over_time` | Believer vs Denier shift across 14 years |
| `vw_tweets_vs_disasters` | Tweet volume joined with disaster events by year |
| `vw_gender_analysis` | Gender breakdown of sentiment and stance |
| `vw_temperature_analysis` | Temperature deviation vs sentiment correlation |
| `vw_geo_tweets` | Geolocated tweets for map visualisation |
| + 6 more views | Monthly, quarterly, sentiment distribution, heatmap etc. |

### 4. Descriptive Analytics (9 Queries)
- Overall dataset summary statistics
- Tweet volume by year with YoY growth
- Stance distribution (Believer / Neutral / Denier)
- Topic distribution across all 10 categories
- Gender breakdown
- Aggressiveness distribution
- Sentiment label distribution (Positive / Neutral / Negative)
- Top 5 most tweeted years
- Disaster events summary

### 5. Diagnostic Analytics (11 Queries)
- Sentiment trend over 14 years
- Stance shift analysis (believer growth vs denier decline)
- Most divisive topics by sentiment standard deviation
- Aggressiveness by topic
- Aggressiveness by stance
- Gender vs sentiment and aggressiveness
- Temperature deviation vs sentiment correlation
- Regional aggressiveness ranking
- Disaster correlation with tweet volume
- Peak tweet hours analysis
- Topic shifts across three time periods

---

## 📈 Key Findings

| Finding | Insight |
|---|---|
| **Believer growth** | Climate believers grew from 16.67% (2006) to 79.40% (2018) |
| **Denier decline** | Climate deniers fell from 8.33% to 6.18% over 14 years |
| **Aggressive discourse** | 28.67% of all 15.7M tweets contain aggressive language |
| **Denier aggression** | Deniers are aggressive 42.65% vs Believers at 27.33% |
| **Paris Agreement effect** | Sentiment turned positive in 2015 (+0.0248) for first time |
| **2018 peak** | 6,259,390 tweets in 2018 — 39.6% of entire 14-year dataset |
| **North America** | Most aggressive region (31.81%) with most deniers (280,236) |
| **Asia** | Least aggressive (17.93%) and most positive (+0.1444) sentiment |
| **Politics topic** | Most aggressive topic at 43.39% — nearly half of all political tweets |
| **Disaster scale** | 2.38 billion people affected by climate disasters in same period |

---

## 🖥️ Dashboard Pages

**Page 1 — Sentiment & Stance Overview**
- 5 KPI cards (Total Tweets, Avg Sentiment, Believers, Deniers, Aggressive Tweets)
- Sentiment trend line chart (2006–2019)
- Stance distribution donut chart
- Believer vs Denier trend over time
- Aggressiveness split donut

**Page 2 — Topic & Aggressiveness Analysis**
- Aggressiveness rate by topic (horizontal bar)
- Average sentiment by topic (horizontal bar)
- Tweet volume by topic (horizontal bar)
- Believers vs Deniers by topic (clustered bar)
- Topic slicer for dynamic filtering

**Page 3 — Regional & Temporal Trends**
- Tweet volume by year (column chart)
- Aggressiveness by continent (horizontal bar)
- Sentiment by continent (horizontal bar)
- Tweet volume vs disaster events over time (line & column)
- Believers vs Deniers by continent (clustered bar)
- Global tweet distribution map
- Year and Continent slicers

---

## 📄 Report Highlights

The analytical report covers:
- Executive Summary with headline findings
- Data Understanding and Schema
- Full Data Cleaning Decision Log
- Descriptive Analytics with 6 data tables
- Diagnostic Analytics with regional and topic breakdown
- 2 Prioritised Recommendations backed by evidence
- Data Quality Notes (missing geolocation, coverage gap)
- Complete Data Dictionary
- References (APA format)

---

## 🚀 How to Run the SQL

1. Install PostgreSQL 15+
2. Create a database called `climate_twitter`
3. Download the dataset from [Mendeley Data](https://data.mendeley.com/datasets/mw8yd7z9wc/2)
4. Open `Climate_Analysis.sql` in pgAdmin or psql
5. Update the file paths in the `\copy` commands to match your local paths
6. Run the file from Part 1 through Part 5 in order

---

## 👩‍💻 About Me

**Balogun Bunmi** — Data Analyst

Skills: SQL | PostgreSQL | Power BI | Python | Excel | Data Cleaning | Data Visualisation | Statistical Analysis

📧 Connect with me on [LinkedIn](#) | 🐙 [GitHub](https://github.com/BUNMI5-design)

---

## 📚 References

- Effrosynidis et al. (2022). The Climate Change Twitter Dataset. *Expert Systems with Applications*, 204, 117541. DOI: [10.1016/j.eswa.2022.117541](https://doi.org/10.1016/j.eswa.2022.117541)
- Budget Office of the Federation: [budgetoffice.gov.ng](https://budgetoffice.gov.ng)

---

*This project was completed as part of the HNG 14 Data Analytics Internship — Stage 4*
