# Superstore Analytics Dashboard - Power BI

This is an interactive dashboard analyzing Sales, Profit, Percentage of Returned Products and the comparison between the updated data versus the data from the previous year (PY). There are also measures responsible for only the PY data.

## Objective

The objective of this project was to compare sales performance versus previous year over time, determine the most profitable product and the most loss making product. Also we had to highlight the sales by its segment and finding out the place where most of the profit is happening given the location.

## Data Source and Preparations

-> Dataset: Superstore Sales from kaggle
-> Cleaned and formatted the dataset using power queries
-> Dax Measures:
     - Sales;
     - Profit;
     - % of Returned Products;
     -  Sales PY;
     -  Profit PY;
     -  % of Returned Products PY;
     -  vs Sales PY;
     -  vs Profit PY;
     -  vs % of Returned Products PY.

## Dashboard Overview

-> KPIs: sales, profit, % of returned products
-> Sales vs PY Over Time
-> Sales by Segment
-> Profit by Product
-> Profit by State

## Key Measures DAX

-> metrics/
  - Percent. Returned Orders =
      - VAR _total_orders = DISTINCTCOUNT( Orders[Order ID] )
      - VAR _returned_orders = DISTINCTCOUNT( Return[Order ID] )
      - VAR _perc = DIVIDE( _returned_orders, _total_orders)
      - RETURN
      - _perc
  - Profit =
      - SUM( Orders[Profit] )
  - Sales =
      - SUM( Orders[Sales] )

-> PY measures/
  - Percent. Returned Orders PY =
      - CALCULATE( [Percent. Returned Orders], SAMEPERIODLASTYEAR(’Date Table’[Date]) )
  - Profit PY =
      - CALCULATE( [Profit], SAMEPERIODLASTYEAR(’Date Table’[Date]) )
  - Sales PY =
      - CALCULATE( [Sales], SAMEPERIODLASTYEAR(’Date Table’[Date]) )

-> vs PY/
  - vs PY - Percent. Returned Orders =
      - [Percent. Returned Orders] - [Percent. Returned Orders PY]
  - vs PY - Profit =
      - DIVIDE( [Profit] - [Profit PY], [Profit PY] )
  - vs PY - Sales =
      - DIVIDE( [Sales] - [Sales PY], [Sales PY] )

## Insights

-> Furnitures are the worst profitable type of product between office supplies and technology;
-> Tables and bookcases are the worst profitable product in the furniture category;
-> California is the most profitable state;
-> Consumer-segment is responsible for leading the sales by segment for over 50% of the cases;
-> Profit was 48,85% higher when compared to the previous year;
-> Sales was 47,16% higher when compared to the previous year;
-> Percentage of returned orders is 2,95% lower when compared to the previous year, meaning that Superstore had a little bit less of loss;
-> Technology is the most profitable product category;
