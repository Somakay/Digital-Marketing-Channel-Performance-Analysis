# Digital-Marketing-Channel-Performance-Analysis
Multi platform ad campaign analysis using Python, R, and Power BI. Covers customer segmentation, CTR trend analysis, correlation analysis, and ROI optimization across Google Ads, Meta Ads, and TikTok Ads
A data analytics project exploring ad campaign performance across three major platforms using Python for data cleaning and segmentation, R for statistical analysis and visualization, and Power BI for the final interactive dashboard.

# Project Overview
This project analyzes 1,800 global ad campaign records from 2024 across Google Ads, Meta Ads, and TikTok Ads. The goal was to identify which platforms, campaign types, and industries drive the strongest return on ad spend, segment campaigns by performance, and surface actionable recommendations for budget optimization and customer retention.
Tools used: Python, R, Power BI
Dataset: 1,800 records across 14 variables covering platforms, industries, countries, and performance metrics
Scope: January 2024 to December 2024 across 7 countries and 5 industries

Dataset
| Column | Description |
|---|---|
| date | Campaign date |
| platform | Google Ads, Meta Ads, TikTok Ads |
| campaign_type | Search, Video, Shopping, Display |
| industry | Fintech, EdTech, Healthcare, SaaS, E-commerce |
| country | 7 countries including USA, UK, UAE, Germany |
| impressions | Total ad impressions |
| clicks | Total clicks |
| CTR | Click through rate |
| CPC | Cost per click |
| ad_spend | Total spend |
| conversions | Number of conversions |
| CPA | Cost per acquisition |
| revenue | Revenue generated |
| ROAS | Return on ad spend |

# Python Analysis
What was done
1. Data loading and exploration
Loaded the raw dataset, checked for missing values (none found across all 14 columns) and confirmed data types before any transformation.
2. Feature engineering

Converted the date column from string to datetime format
Extracted month, day, quarter, and year as separate columns
Calculated profit as revenue minus ad spend, revealing 136 campaigns running at a loss

3. Channel performance analysis
Grouped all 1,800 campaigns by platform and aggregated total spend, revenue, profit, conversions, clicks, impressions, average CTR, ROAS, CPC, and CPA to compare platform level performance.
4. Customer segmentation using KMeans clustering
Selected CTR, CPA, and ROAS as clustering features because they measure three non-overlapping dimensions of performance — ad engagement, conversion efficiency, and return on spend. Applied StandardScaler to normalize the features before clustering, then ran KMeans with 3 clusters. Segments were labeled by average ROAS:

| Segment | Avg ROAS | Campaign Count |
|---|---|---|
| Low ROAS | 1.48 | 285 (15.8%) |
| Medium ROAS | 5.31 | 516 (28.7%) |
| High ROAS | 11.41 | 999 (55.5%) |

5. PCA visualization
Used Principal Component Analysis to compress the 3D feature space down to 2 dimensions for plotting, confirming that the three segments are genuinely distinct and not overlapping.
6. Export
Cleaned and segmented dataset exported as ads_clean.csv for use in R and Power BI.

# R Analysis
What was done
1. CTR trend analysis
Grouped campaigns by month and platform to track how click through rates changed across the year for all three platforms. Visualized using a line chart with ggplot2.
2. ROI by campaign type
Compared average ROAS across Search, Video, Shopping, and Display campaigns broken down by platform, identifying which campaign formats deliver the strongest return per platform.
3. Correlation analysis
Built a correlation matrix across all nine numeric variables using corrplot to understand relationships between metrics and identify which inputs most strongly drive revenue outcomes.
4. Segment performance by platform
Visualized how Low, Medium, and High ROAS segments are distributed across the three platforms, showing which platforms produce the most high performing campaigns.

# Power BI Dashboard
3 pages covering:
Page 1 — Campaign Overview

- KPI cards: Total Revenue ($54.2M), Total Conversions (327K), Total Ad Spend ($11.1M), Average ROAS (6.45), Total Profit ($43.1M)
- Average ROAS by Platform and Campaign Type
- Monthly Revenue Trend by Platform
- Segment Breakdown (High / Medium / Low ROAS)

Page 2 — Profitability & Segment Analysis

- Profit by Platform
- Average ROAS by Industry and Campaign Type (matrix heat map)
- Conversions by Industry and Segment
- Interactive slicers: Platform, Country, Industry, Quarter, Segment

Page 3 — ROI & Country Analysis

- Revenue by Country (map visual)
- Revenue by Country and Platform
- Conversion Trend by Quarter and Campaign Type
- Ad Spend vs Revenue scatter plot

# Key Findings
Platform performance:

- TikTok Ads leads in both total profit ($17.6M) and average ROAS, making it the strongest performing platform overall
- Google Ads comes in second at $15.7M profit, closely behind TikTok
- Meta Ads generates the least profit at $9.8M despite comparable spend levels, suggesting inefficient budget allocation

Segmentation:

- 55.5% of campaigns fall in the High ROAS segment, returning an average of 11.41x spend
- Only 15.8% of campaigns are Low ROAS, but their average return of just 1.48x represents significant budget waste
- The 7x ROAS gap between High and Low performing segments confirms that uniform budget allocation across all campaigns is suboptimal

Industry insights:

- SaaS leads in average ROAS at 6.65, driven by strong Search campaign performance (7.36)
- EdTech Search campaigns are the single highest performing combination at 8.11 average ROAS
- E-commerce has the lowest total ROAS at 6.13, suggesting it needs a different channel strategy

Country insights:

- UAE generates the highest revenue of all 7 countries, followed closely by Australia
- USA generates the lowest revenue despite being a major advertising market, pointing to higher competition and cost

Quarterly trends:

- Video campaign conversions surge dramatically in Q4, suggesting seasonal demand that could be better capitalised on with increased Video budgets heading into Q4
- Search campaigns are the most consistent converter across all four quarters

Ad spend efficiency:

- Meta Ads is an outlier on the scatter plot — higher spend relative to revenue compared to TikTok and Google, confirming it delivers the weakest ROI per dollar spent

# How to Run
Python
- pip install pandas numpy scikit-learn matplotlib
- jupyter notebook digital_marketing_campaign.ipynb

R
- Open Digital_Marketing_Channel_Performance_Analysis.Rmd in RStudio and knit to HTML, or run each chunk individually. Required packages:
- install.packages(c("tidyverse", "ggplot2", "corrplot", "scales", "lubridate"))
  
Power BI
- Load digital marketing campaign_cleaned.csv into Power BI Desktop. All visuals are built from this single table.

# About
Built as part of a data analytics portfolio by Kay Okerulu Somadina, a Master of Data Analytics student at the University of Niagara Falls, Ontario. This project demonstrates an end to end analytical workflow across Python, R, and Power BI with a focus on marketing performance, customer segmentation, and ROI optimization.

Connect on LinkedIn | GitHub
