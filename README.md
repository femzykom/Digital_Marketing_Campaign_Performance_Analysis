# 📊 Digital Marketing Campaign Performance Analysis

**Tools**: Excel, SQL, Power BI  
**Duration Analyzed**: 28 Days  
**Campaigns**: 11 across Facebook, Instagram, Google, and YouTube  

---
## Table of Contents
- [Project Summary](#project-summary)
- [Objectives](#objectives)
- [Dataset Overview](#dataset-overview)
- [Tools & Technologies](#tools-&-technologies)
- [Data Cleaning & Preparation](#data-cleaning-&-preparation)
- [SQL Snippet – ROAS Per Day](#SQL-snippet-–-rOAS-per-day)
- [Key Insights](#key-insights)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
- [References](#References)

## 📌 Project Summary

This project analyzes the performance of 11 digital advertising campaigns using real-world marketing KPIs. The goal is to uncover data-driven insights that support strategic budget decisions, identify cost-efficiency across channels, and improve conversion outcomes.

> **Key Metrics:** ROAS, ROMI, CTR, CPC, CAC, CTO

![Digital Marketing Report 4b](https://github.com/user-attachments/assets/a24c90ba-0f4e-4954-b84a-a200d72fa12d)

---

## 🧠 Objectives

- Evaluate marketing ROI across platforms and campaigns
- Identify top-performing and underperforming channels
- Understand conversion behavior across the funnel
- Deliver actionable insights through visual dashboards

---

## 🗂️ Dataset Overview

**Source**: Kaggle  
**File**: `Digital_Marketing_Metrics_&_KPIs_to_Measure.csv`

| Column Type       | Description                              |
|-------------------|------------------------------------------|
| Campaign Info     | Name, Category, Date, ID                 |
| Engagement Metrics| Impressions, Clicks, Leads, Orders       |
| Financial Metrics | Revenue, Mark_Spent (Ad Spend)           |

---

## 🛠️ Tools & Technologies

| Tool      | Purpose                          |
|-----------|----------------------------------|
| **Excel** | Initial cleaning and formatting  |
| **MySQL** | Data analysis and transformation |
| **Power BI** | Interactive dashboard and visuals |

---

## 🧹 Data Cleaning & Preparation

- Standardized column headers
- Converted all currency fields to ₦ (Naira)
- Handled zero-divisions in KPIs
- Calculated key metrics (ROAS, ROMI, CTO, CAC)

---

## 📈 SQL Snippet – ROAS Per Day

```sql
SELECT 
    c_date, campaign_name, category, campaign_id,
    impressions, mark_spent, clicks, leads, 
    orders, revenue,
    CASE 
        WHEN mark_spent = 0 THEN 0 
        ELSE revenue / mark_spent 
    END AS ROAS
FROM Digital_Table
WHERE clicks IS NOT NULL;
```
---

## 🔍 Key Insights
### 🎯 Top-Performing Campaign
#### YouTube Blogger (Influencer)
-	ROAS: 3.77 | ROMI: 2.8 | CAC: ₦114
-	Gross Profit: ₦606.3K

### 🚨 Lowest-Performing Campaign
#### Facebook Lal (Social)
-	ROAS: 0.11 | ROMI: –0.9
-	Gross Loss: –₦126.2K
### 💡 Conversion Insights
-	CTR range: 0.9% – 3.1%
-	CTO range: 0.17% – 0.35%
-	High engagement didn’t always lead to high conversion
-	Influencer channels showed best ROI across funnel

---

### 📊 Recommendations
1. Scale Influencer Campaigns:
- Youtube Blogger and similar influencer strategies delivered high ROMI and efficient CAC — ideal for scalable investment.

2. Reassess or Retire Social Campaigns:
- Channels like Facebook Lal performed poorly despite high Spend. Testing new audience segments or creatives may be necessary.

3. Investigate CPC Inefficiencies:
- High CPC outliers (₦1.19+) require creative/bidding optimizations. Consider narrowing target demographics or testing shorter campaign durations.

4. Funnel Optimization:
- Low conversion from leads to orders in certain campaigns suggests friction points. Review landing page UX, CTA clarity, and checkout flows.

5. Continue Daily CTO Monitoring:
- The day-level CTO trend has been embedded in the dashboard, allowing for real-time tracking and mid-campaign optimization opportunities.


---

### ⚠️ Limitations
- The analysis assumes marketing costs are limited to ad spend (i.e., excludes fixed costs like salaries or tech tools).
- ROAS and ROMI were calculated at campaign level only; customer lifetime value (CLV) not included.
- The dataset represents a snapshot in time; seasonal or external influences were not modeled.
- Single campaign window (no seasonality or A/B testing)


---

### 📚 References
-	Dataset: [Kaggle](www.kaggle.com)
-	Formula References: [OWOX](https://www.owox.com/blog/articles/digital-marketing-metrics-and-kpis)

