# Retail Vendor & Inventory Analysis

## Project Overview
This project analyzes retail and wholesale vendor performance, inventory, and sales data to optimize profitability. It identifies underperforming brands, top vendors, bulk purchasing effects, inventory turnover, and profitability variances.

## Business Problem
Inefficient pricing, poor inventory turnover, and vendor dependency can reduce profitability.

## Objectives
- Identify brands needing promotional or pricing adjustments  
- Determine top vendors contributing to sales and gross profit  
- Analyze bulk purchasing effects on unit costs  
- Assess inventory turnover and capital locked in unsold inventory  
- Compare profitability of high vs. low-performing vendors  

## Tech Stack
- Python (pandas, numpy, matplotlib, seaborn, scipy, SQLAlchemy)  
- SQLite for database  
- Jupyter Notebook / Python scripts for analysis and visualization  

## Vendor Summary Creation
- Merge purchases, sales, purchase prices, and freight data  
- Create `vendor_sales_summary` table  
- Clean data: handle missing values, whitespace, convert volume to numeric  
- Add computed columns: GrossProfit, ProfitMargin, StockTurnover, SalesToPurchaseRatio  
- Store cleaned summary in database  

## Exploratory Data Analysis & Insights
- Analyze numerical and categorical distributions, detect outliers  
- Explore relationships and correlations between key metrics  
- Identify:
  - Brands with low sales but high margins (for promotions/pricing)  
  - Top vendors and brands by sales and purchase contributions  
  - Bulk purchasing impact on unit cost  
  - Vendors with low inventory turnover  
  - Capital locked in unsold inventory  
- Visualizations include: scatter plots, bar charts, Pareto chart, boxplots, histograms, donut chart, and correlation heatmap  

## Statistical Analysis
- Confidence intervals for profit margins of top vs. low-performing vendors  
- Two-sample t-test confirms significant differences in profit margins  

## Key Findings
- 198 brands have low sales but high margins → candidates for promotion/price optimization  
- Top 10 vendors contribute ~65% of total purchases → potential supply chain risk  
- Bulk purchasing reduces unit costs by ~72% → higher profitability if managed efficiently  
- Low inventory turnover vendors tie up $2.71M in unsold capital → optimize stock and purchase quantities  
- High-margin vendors have low sales → focus on marketing, distribution, or pricing strategies  

## Recommendations
- Re-evaluate pricing and promotions for low-sales, high-margin brands  
- Diversify vendor partnerships to reduce dependency  
- Leverage bulk purchase advantages for cost savings  
- Optimize slow-moving inventory with clearance sales or adjusted orders  
- Improve marketing & distribution for low-performing vendors  

## Outputs
- Cleaned vendor summary: `vendor_sales_summary.csv`  
- Visualizations & plots saved within analysis script  
- Logs: `logs/ingestion_db.log`, `logs/get_vendor_summary.log`

## Project Pipeline

```mermaid
flowchart TD
    A[Raw CSV Data] --> B[Data Ingestion]
    B --> C[SQLite Database]
    C --> D[Vendor Summary Creation]
    D --> E[Data Cleaning and Feature Engineering]
    E --> F[Exploratory Data Analysis - EDA]
    F --> G[Statistical Analysis and Insights]
    G --> H[Key Findings and Recommendations]
    H --> I[Outputs]
    
    classDef process fill:#cce5ff,stroke:#333,stroke-width:1px,color:#000
    classDef output fill:#b3e6b3,stroke:#333,stroke-width:1px,color:#000

    class B,D,E,F,G,H process
    class I output
