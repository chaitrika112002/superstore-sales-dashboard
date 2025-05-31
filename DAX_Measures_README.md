# DAX Measures Reference for Superstore Sales Dashboard

This file contains all the DAX measures and calculated columns used in the Superstore Sales Power BI project. These measures support the star schema model and enable key sales, profit, and time intelligence calculations.

---

## Date Dimension Calculated Columns

These calculated columns enrich the `DimDate` table for time intelligence and filtering:

- **Day**
  ```DAX
  Day = DAY(DimDate[Date])
  ```
  Extracts the day number from the date.

- **MonthName**
  ```DAX
  MonthName = FORMAT(DimDate[Date], "MMMM")
  ```
  Returns the full month name (e.g., January).

- **MonthNumber**
  ```DAX
  MonthNumber = MONTH(DimDate[Date])
  ```
  Extracts the month number (1-12) for sorting.

- **Quarter**
  ```DAX
  Quarter = "Q" & FORMAT(DimDate[Date], "Q")
  ```
  Returns the quarter in the format Q1, Q2, etc.

- **Weekday**
  ```DAX
  Weekday = FORMAT(DimDate[Date], "dddd")
  ```
  Returns the full weekday name (e.g., Monday).

- **Year**
  ```DAX
  Year = YEAR(DimDate[Date])
  ```
  Extracts the year from the date.

- **YearMonth**
  ```DAX
  YearMonth = FORMAT(DimDate[Date], "YYYY-MM")
  ```
  Returns year and month in YYYY-MM format, useful for time series.

---

## FactOrders Table Measures

Measures that summarize and analyze sales, profit, and quantity:

- **Total Sales**
  ```DAX
  Total Sales = SUM('FactOrders'[Sales])
  ```
  Calculates total sales.

- **Total Profit**
  ```DAX
  Total Profit = SUM('FactOrders'[Profit])
  ```
  Calculates total profit.

- **Total Quantity**
  ```DAX
  Total Quantity = SUM('FactOrders'[Quantity])
  ```
  Calculates total quantity sold.

- **% of Total Sales**
  ```DAX
  % of Total Sales = DIVIDE(
      SUM('FactOrders'[Sales]),
      CALCULATE(SUM('FactOrders'[Sales]), ALL('FactOrders'))
  )
  ```
  Calculates the current sales as a percentage of overall sales (ignoring filters).

- **Profit Margin**
  ```DAX
  Profit Margin = DIVIDE([Total Profit], [Total Sales], 0)
  ```
  Calculates profit margin (profit divided by sales).

- **Sales YoY**
  ```DAX
  Sales YOY = CALCULATE(
      [Total Sales],
      SAMEPERIODLASTYEAR('FactOrders'[Order Date])
  )
  ```
  Calculates sales for the same period in the previous year.

- **Cumulative Sales**
  ```DAX
  Cumulative Sales = CALCULATE(
      [Total Sales],
      FILTER(
          ALLSELECTED('FactOrders'[Order Date]),
          'FactOrders'[Order Date] <= MAX('FactOrders'[Order Date])
      )
  )
  ```
  Calculates running total of sales up to the current date.

---

## Ranking and Top N Measures

Measures to find top-performing categories, products, and regions:

- **Best Selling Category**
  ```DAX
  Best Selling Category = CALCULATE(
      MAX('FactOrders'[Category]),
      TOPN(
          1,
          SUMMARIZE(
              'FactOrders',
              'FactOrders'[Category],
              "TotalSales", SUM('FactOrders'[Sales])
          ),
          [TotalSales],
          DESC
      )
  )
  ```
  Returns the category with the highest total sales.

- **Top Product**
  ```DAX
  Top Product = CALCULATE(
      MAX('FactOrders'[Product Name]),
      TOPN(
          1,
          SUMMARIZE(
              'FactOrders',
              'FactOrders'[Product Name],
              "TotalSales", SUM('FactOrders'[Sales])
          ),
          [TotalSales],
          DESC
      )
  )
  ```
  Returns the product with the highest total sales.

- **Top Region**
  ```DAX
  Top Region = CALCULATE(
      MAX('FactOrders'[Region]),
      TOPN(
          1,
          SUMMARIZE(
              'FactOrders',
              'FactOrders'[Region],
              "Total Sales",
              [Total Sales]
          ),
          [Total Sales],
          DESC
      )
  )
  ```
  Returns the region with the highest total sales.

---

## Usage Notes

- These DAX expressions are designed to work within a star schema where `FactOrders` is the fact table connected to dimension tables (`DimDate`, `DimProduct`, `DimCustomer`, `DimLocation`).
- Date-based measures use `FactOrders[Order Date]` for time intelligence.
- Use these measures in visuals such as cards, charts, tables, and slicers to enable interactive reports.
- The `% of Total Sales` measure uses the `ALL` function to calculate total sales regardless of filters.
