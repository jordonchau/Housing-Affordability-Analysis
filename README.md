# Housing Affordability Analysis Across New York and New Jersey

## Project Overview

This project analyzes housing affordability across ZIP codes in New York and New Jersey by combining rental market data from Zillow with household income data from the U.S. Census Bureau. The objective was to evaluate how affordable housing is across different regions by calculating a rent burden metric and identifying areas with the highest and lowest affordability.

The analysis integrates multiple data sources, performs data cleaning and transformation, and presents findings through an interactive Power BI dashboard.

---

## Business Problem

Housing affordability continues to be a major challenge for many households. Understanding the relationship between rent prices and household income can help identify regions experiencing the greatest financial strain.

This project aims to answer the following questions:

- Which ZIP codes are the most affordable and least affordable?
- How does household income relate to rental costs?
- Which regions experience the highest rent burden?
- Are there significant affordability differences across New York and New Jersey?

---

## Data Sources

### Zillow Rental Data
- Source: Zillow Observed Rent Index (ZORI)
- Contains median rental prices by ZIP code.
- Data was filtered to include only ZIP codes in New York and New Jersey.

### U.S. Census Bureau Data
- Source: American Community Survey (ACS) 2024 5-Year Estimates
- Table Used: B19013 — Median Household Income
- Contains median household income estimates by ZIP Code Tabulation Area (ZCTA).

---

## Tools & Technologies

- **Python**
  - pandas
  - matplotlib
  - sqlite3

- **SQL**
  - SQLite

- **Excel**
  - Data cleaning and preprocessing

- **Power BI**
  - Interactive dashboard development

---

## Methodology

### 1. Data Cleaning & Preparation

The Zillow rental dataset contained rental observations for ZIP codes across the United States. The dataset was filtered to retain only New York and New Jersey ZIP codes.

Data preparation tasks included:

- Removing unnecessary columns.
- Handling missing values.
- Cleaning and standardizing ZIP code formats.
- Filtering observations to NY and NJ only.
- Preparing Census income data in Excel.

### 2. Data Integration

The cleaned Zillow rental dataset was merged with U.S. Census household income data using ZIP codes as the common key.

The merged dataset included:

- ZIP Code
- State
- City
- County
- Median Monthly Rent
- Median Household Income

### 3. Feature Engineering

A new metric, **Rent Burden Percentage**, was created to measure housing affordability.

Formula:

```text
Rent Burden (%) = (Median Monthly Rent × 12 / Median Household Income) × 100

Rent burden measures the percentage of annual household income required to cover annual housing costs.

SQL Analysis

SQLite was used to store and query the merged housing dataset.

Example analyses included:

Calculating average rent by state.
Identifying the most affordable ZIP codes.
Identifying the least affordable ZIP codes.
Exploring relationships between income and rent.

Example query:

SELECT ZIPCode,
       City,
       MedianIncome,
       `Median Rent`,
       RentBurdenPct
FROM housing_data
ORDER BY RentBurdenPct ASC
LIMIT 10;
Dashboard Features

The Power BI dashboard includes:

KPI Cards
Average Monthly Rent
Average Household Income
Average Rent Burden
Interactive Filters
Filter by State
Filter by County
Visualizations
Top 10 Most Affordable ZIP Codes
Top 10 Least Affordable ZIP Codes
Median Household Income vs Monthly Rent Scatter Plot

Key Insights
The average monthly rent across New York and New Jersey ZIP codes was approximately $3,230.
The average household income across analyzed ZIP codes was approximately $104,000.
The average rent burden across both states was approximately 38.7%, exceeding the commonly recommended affordability threshold of 30%.
Higher-income ZIP codes generally experienced higher monthly rents, indicating a positive relationship between income and housing costs.
Several luxury and seasonal housing markets, particularly in the Hamptons region, exhibited extremely high rent burden percentages due to exceptionally high rental prices.
The most affordable ZIP codes experienced rent burdens near 15%, while some outlier ZIP codes exceeded 100%, highlighting significant affordability disparities.

Dashboard Preview
<img width="2000" height="1140" alt="image" src="https://github.com/user-attachments/assets/ac29e76b-2cb0-416c-b7c2-75e88f0a8d71" />

Project Structure
housing-affordability-analysis/
│
├── data/
│   ├── zillow_rent_data.csv
│   ├── census_income_data.csv
│   └── merged_housing_data.csv
│
├── notebooks/
│   └── Housing_Affordability_Analysis.ipynb
│
├── sql/
│   └── housing_queries.sql
│
├── dashboard/
│   └── Housing_Affordability_Dashboard.pbix
│
├── images/
│   └── dashboard.png
│
└── README.md

Future Improvements
Expand the analysis to all U.S. states.
Incorporate additional socioeconomic indicators such as poverty rates and unemployment.
Add geographic mapping visualizations.
Develop predictive models to forecast future housing affordability trends.

