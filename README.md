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
| Post_ID                | Unique ID for all posts   |
| Platform                | Social media platform (TikTok, LinkedIn, YouTube etc.)   |
| Content_Type            | Organic or Promoted                              |
| Content_Category        | Product Promotion, Customer Story, Event/Webinar, Educational, Entertainment        |
| Post_Type               | Video, Carousel, Text, Article, Live Stream, PDF, Image,          |
| Region, Latitude, Longitude | Geographic info                                |
| Post_Published_At, Hour, Day | Publishing timestamp                         |
| Engagement, Views, Likes, Shares, CTR, Impressions, Clicks | Performance metrics           |
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
- Youtube recorded the highest engagement across various content category, the least was linkedIn
- TikTok had the highest engagement rate, especially for short-form videos.
- Educational content performed better on LinkedIn and X.com.
- Carousels generated more engagement on LinkedIn followed by instagram, no engagement for other platform.
- Images generated more engagement on instagram and linkedIn, least on Youtube
- Video generated more engagement on Tiktok followed closely by YouTube & instagram, least is LinkedIn
- Live streams had more engagement on instagram followed closely by facebook, the least is LinkedIn no engaagement on X.com. X.com generated the highest engagement for text.

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
- Canada experienced a consistent increase in CTR, Japan and India experienced a drop.
- Engagement peaked between 11 AM and 2 PM (local time).
- Weekdays Friday in 14 & 18 hours yielded the highest engagement, while 19 hour yielded the lowest, other low engagement occurs on monday 14 hour, tuesday 14 hour.


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
INTERACT WITH REPORT HERE: [CLICK HERE](https://app.powerbi.com/view?r=eyJrIjoiNGQ3ZDI3ZTUtZTE0YS00Y2VmLThjM2EtOWJmMDYwZTliYzgwIiwidCI6IjQ2NTRiNmYxLTBlNDctNDU3OS1hOGExLTAyZmU5ZDk0M2M3YiIsImMiOjl9)

VIEW ON LINKEDIN : [CLICK HERE](https://www.linkedin.com/posts/emmanuel-idowu-analyst_datadna-builtwithzoomcharts-dataanalyst-activity-7343870697812733952-ogVX)
---
## 📊 DAX Measures Used

```DAX
-- Engagement Rate
Engagement Rate = 
DIVIDE([Total Engagement] ,[Total Impression],0)

-- Average CTR
Average CTR = 
AVERAGE('Data'[Click_Through_Rate])

-- Avg Engagement
Avg Engagement = 
AVERAGE('Data'[Engagement])

-- Total Clicks
Total Clicks = SUM(Data[Clicks])

-- Total Post
Total Post = 
DISTINCTCOUNT('Data'[Post_ID])

--Total Engagement
Total Engagement = SUM(Data[Engagement])

--Total Impression
Total Impression = SUM(Data[Impressions])

--Total Live Streams
Total Live Stream = SUM(Data[Live_Stream_Views])

--Total Video Views
Total Video Views = SUM(Data[Video_Views])

