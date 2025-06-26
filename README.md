# 📊 Social Media Marketing Performance Analytics Report (2024)

This Power BI report provides a detailed exploratory analysis of a global IT company's 2024 social media campaigns across TikTok, Instagram, LinkedIn, and X.com. The goal is to uncover what drives content success, identify regional engagement trends, and inform content/platform strategy decisions.

---

## 🔍 Objectives

- Identify top-performing platforms and post types
- Reveal content categories that drive engagement across regions
- Understand how performance varies by post format, time, and hashtags
- Determine the best days and times to post for maximum engagement
- Evaluate promoted vs. organic content performance
- Analyze hashtag effectiveness on impressions and clicks

---

## 📂 Dataset Overview

| Column Name             | Description                                      |
|-------------------------|--------------------------------------------------|
| Platform                | Social media platform (TikTok, LinkedIn, etc.)   |
| Content_Type            | Organic or Promoted                              |
| Content_Category        | Product Promo, Educational, Entertainment        |
| Post_Type               | Video, Carousel, Text                            |
| Region, Latitude, Longitude | Geographic info                                |
| Post_Published_At, Hour, Day | Publishing timestamp                         |
| Engagement, Views, CTR, Impressions, Clicks | Performance metrics           |
| Main_Hashtag            | Primary hashtag used                             |

---

## 📄 Report Structure (3 Pages)

### 📘 Page 1: **Platform & Content Performance Overview**
**Goal**: Identify what kind of content works best and on which platform. It screams which platform-format combos TRULY pull weight.

#### 🔹 Visuals:
- **KPI Cards**: Total Posts, Total Impressions, Total Views, Total Engagement, Avg Engagement Rate, Avg CTR
- **Drill-Down Column Chart**: Avg Engagement, Views, and Rate by Platform → Post Type → Content Type
- **100% Stacked Bar**: Avg Engagement by Content Category → Post Type → Platform
- **Scatter Plot**: Engagement Rate vs Total Impressions by Platform → Day → Hour
- **Matrix**: Engagement Rate by Platform (rows) and Post Type (columns)

#### 🔧 Drilldowns:
- Platform → Post Type → Content Type
- Platform → Day of Week → Hour

#### 📈 Insights:
- TikTok had the highest engagement rate, especially for short-form videos.
- Educational content performed better on LinkedIn and X.com.
- Carousels generated more engagement on Instagram than videos.
- Lower engagement was observed during off-peak hours (12 am–6 am).

![Screenshot_5](https://github.com/user-attachments/assets/68a11d64-edd8-4168-b6f7-d8a05bb8d6a6)
---

### 📘 Page 2: **Regional & Temporal Trends**
**Goal**: Explore when and where posts perform best. It cleanly separates “reach waves” from “quality tides” while exposing reliable time slots.

#### 🔹 Visuals:
- **KPI Cards**: Same as Page 1
- **Time Series**: Total Engagement and Views by Date Hierarchy
- **Map**: Total Video Views by Region
- **Matrix Heatmap**: Avg Engagement (Rows = Hour, Columns = Day Name)
- **Line & Clustered Column (Small Multiples)**: Avg Engagement (columns) and Avg CTR (line) over Time (Parameter-driven: Year, Quarter, Month), broken by Region

#### 🧠 Parameters:
- **Date Period Parameter**: Enables switching between Year, Quarter, and Month views.

#### 📈 Insights:
- Canada experienced a consistent increase in CTR 
- Engagement peaked between 11 AM and 2 PM (local time).
- Weekdays Friday in 14 & 18 hours yielded the highest engagement, while 19 hour yielded the lowest, other low engagement occurs on monday 14 hour, tuesday 14 hour.
- Regions with low post volume often had erratic CTR trends — visualized using a **heat+bar matrix**.
![Screenshot_6](https://github.com/user-attachments/assets/4de59f54-0906-4407-aaed-1a07eba0dba5)
---

### 📘 Page 3: **Hashtag & Strategy Deep Dive**
**Goal**: Analyze hashtag effectiveness and content type impact. It pivots from vanity volume to efficiency, surfacing the hashtags and paid tactics that punch above their weight.

#### 🔹 Visuals:
- **KPI Cards**: Total Views, Tota Video Views, Total Live Streams, Total Engagement, Avg Engagement Rate, Avg CTR
- **Bar Chart**: Top 10 Hashtags by Clicks
- **Scatter Plot**: Engagement Rate vs Total Impressions (Main Hashtag) → Platform → Day → Hour
- **Clustered Column Chart**: Total Video Views vs Live Streams by Platform → Content Type
- **Stacked Bar**: Total Engagement by Content category (Legend: Engagement Level)
- **Matrix with Sparkline**: Regional metrics with engagement trend by month

#### 📈 Insights:
- Hashtags like `#ProductDemp`, `#CustomerStory`, and `#TrendingNow` generated the highest CTR.
- Medium engagement level contents outperformed high and low engagement levels in terms of engagement rate for content category.
- Regions with consistent monthly growth (sparkline) showed strong hashtag loyalty and timing adherence.
- Youtube had the highest live streams and video views, X.com had no live stream and linkedIn had the least video view
![Screenshot_7](https://github.com/user-attachments/assets/6a807041-3998-4df3-b332-54011f1e0d2e)
---

## 📊 DAX Measures Used

```DAX
-- Engagement Rate
Engagement Rate = 
DIVIDE(SUM('Data'[Engagement]), SUM('Data'[Impressions]))

-- Average CTR
Average CTR = 
AVERAGE('Data'[Click_Through_Rate])

-- Avg Engagement
Avg Engagement = 
AVERAGE('Data'[Engagement])

-- Post Count
Post Count = 
COUNT('Data'[Post_ID])

-- Sparkline Value (monthly aggregation)
Monthly Engagement = 
CALCULATE(SUM('Data'[Engagement]), DATESMTD('Data'[Post_Date]))
