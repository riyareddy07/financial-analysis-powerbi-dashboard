# Power BI Financial Analysis Dashboard

This project provides an **interactive Power BI dashboard** to analyze financial performance, including **sales, profit, orders, and discount trends** across different segments, countries, and products. The dashboard is built using **Power BI** with **DAX calculations** and **Time Intelligence functions** for advanced insights.

---

## Data Preprocessing

To ensure data quality and accurate analysis, the following preprocessing steps were performed:
- ** Data Cleaning:** Transposed data for better visualization, removed unwanted missing rows and columns.
- ** Data Profiling:** Identified **anomalies, missing values, duplicates, and null values** in Power BI.
- ** Data Transformation:** Applied **DAX calculations** for financial KPIs and trend analysis.

  ![![image](https://user-images.githubusercontent.com/97775044/215146486-101d3195-4313-4c29-b88e-b8758d513911.png)
](https://github.com/riyareddy07/financial-analysis-powerbi-dashboard/blob/main/Screenshot%202025-03-02%20121231.png)


---

## Key Insights & Findings

###  Financial Performance Overview
- ** Total Profit:** **$92,311,095** (+249.46% YoY Growth)
- ** Total Sales:** **$13,015,238**
- ** Total Discount Given:** **7,059,717**
- ** Total Orders :** **$861,132**

###  Profit Margin by Country
- ** Canada:** **$247.43K**
- ** France:** **$240.93K**
- ** United States:** **$232.63K**
- ** Mexico:** **$203.33K**
- ** Germany:** **$201.49K**

###  Sales & Orders Analysis
- ** Orders by Country:** U.S., France, and Canada have the highest order volumes.
 ![![image](https://user-images.githubusercontent.com/97775044/215146486-101d3195-4313-4c29-b88e-b8758d513911.png)
](https://github.com/riyareddy07/financial-analysis-powerbi-dashboard/blob/main/F-1.png)

- ** Discount Trends:** High discount levels (57.8%) impact profitability.
  ![![image](https://user-images.githubusercontent.com/97775044/215146486-101d3195-4313-4c29-b88e-b8758d513911.png)
](https://github.com/riyareddy07/financial-analysis-powerbi-dashboard/blob/main/F-3.png)

###  Product & Segment Performance
- **Top-Selling Products:**
  1. ** Paseo** - **$33,011.1K**
  2. ** VTT** - **$20,511.9K**
  3. ** Velo** - **$18,250.1K**
  ![![image](https://user-images.githubusercontent.com/97775044/215146486-101d3195-4313-4c29-b88e-b8758d513911.png)
](https://github.com/riyareddy07/financial-analysis-powerbi-dashboard/blob/main/F-6.png)

- ** Profitability by Customer Segment:**
  - ** Channel Partners:** Highest profit margins (**73.68%**)
  - ** Midmarket:** Moderate profitability (**28.90%**)
  - ** Enterprise:** Negative margins (-3.1% to -6.95%)
  ![![image](https://user-images.githubusercontent.com/97775044/215146486-101d3195-4313-4c29-b88e-b8758d513911.png)
](https://github.com/riyareddy07/financial-analysis-powerbi-dashboard/blob/main/F-5.png)
---

## Data Analytics Methods

###  1. Anomaly Detection
- ** Irregularities detected in sales and profit data across segments.**
- ** Unusual fluctuations in order volumes and discount applications.**

####  DAX Calculation for Anomaly Detection
```DAX
Anomaly Detection = 
VAR MeanSales = AVERAGE('Financials'[Sales Amount])
VAR StdDevSales = STDEV.P('Financials'[Sales Amount])
VAR UpperBound = MeanSales + (2 * StdDevSales)
VAR LowerBound = MeanSales - (2 * StdDevSales)
RETURN 
    IF(
        'Financial Sample'[Sales Amount] > UpperBound || 'Financial Sample'[Sales Amount] < LowerBound,
        "Anomaly", "Normal"
    )
```

---

###  2. Financial Trend Analysis

####  Business Problem
To enable **data-driven decision-making** by tracking financial performance trends over time and optimizing:
- ** Revenue Growth Strategies**
- ** Discount Optimization**
- ** Customer Segment Profitability**

####  Key Findings
- ** Discounts negatively impact overall profit margins.**
- ** Sales show seasonal variations, requiring strategy adjustments.**
- ** Enterprise segment shows negative profitability, requiring corrective actions.**

####  DAX Calculations for Key Metrics
#####  Total Sales Calculation
```DAX
Sales Amount = SUM(Financials[Sales Amount])
```
##### Profit Margin Calculation
```DAX
Profit Margin = DIVIDE([Profit], [Sales Amount])*100
```
#####  Discount Impact Analysis
```DAX
Discount Effect = 
VAR AvgDiscount = AVERAGE('Financials'[Discount])
RETURN 
    IF(AvgDiscount > 0.2, "High Discount Impact", "Low Discount Impact")
```

---

###  3. Time Intelligence Analysis

####  DAX Time Intelligence Calculations for Financial Trends
#####  Year-over-Year (YoY) Sales Growth
```DAX
YoY Sales Growth = 
VAR PriorYearSales = CALCULATE([Sales Amount], SAMEPERIODLASTYEAR('Date'[Date]))
RETURN 
    DIVIDE([Sales Amount] - PriorYearSales, PriorYearSales, 0)
```
#####  Month-to-Date (MTD) Sales
```DAX
Sales MTD = TOTALMTD([Sales Amount], 'Date'[Date])
```
##### Quarter-to-Date (QTD) Sales
```DAX
Sales QTD = TOTALQTD([Sales Amount], 'Date'[Date])
```
#####  Year-to-Date (YTD) Sales
```DAX
Sales YTD = TOTALYTD([Sales Amount], 'Date'[Date])
```
##### Cumulative Sales Over Time
```DAX
Cumulative Sales = 
CALCULATE(
    [Sales Amount],
    FILTER(
        ALL('Date'),
        'Date'[Date] <= MAX('Date'[Date])
    )
)
```

---

##  Dashboard Features
**Interactive Filters** for dynamic data exploration.  
**YoY Comparisons** for financial performance tracking.  
**Segment-wise Profitability Reports** to evaluate business impact.  
**DAX Calculations & Time Intelligence** for enhanced analytics.  


---

##  How to Use
1. ** Download** the dataset (`Financial Sample.xlsx`).  
2. ** Open** `Financial Analysis.pbix` in Power BI.  
3. ** Interact** with the dashboard using filters to explore insights.  
4. ** Analyze** sales trends, profit margins, and order distributions.  

---

##  Conclusion
This **Power BI dashboard** provides deep insights into **financial trends, sales performance, and discount impacts**, allowing businesses to make **data-driven decisions**. Using **DAX calculations and Time Intelligence functions**, this report delivers **actionable insights** to optimize revenue, discount strategies, and segment profitability.  

---

##  Contributing
Feel free to **contribute** by:
- ** Enhancing visualizations** with additional insights.  
- ** Adding advanced DAX calculations** for deeper analysis.  
- ** Integrating additional datasets** for broader comparisons.  

---

##  License
This project is **open-source** and available for educational and analytical purposes.  

---

##  Acknowledgments
Special thanks to **Power BI and DAX experts** for enabling **data-driven insights** through **advanced analytics and visualization techniques**.  

---

