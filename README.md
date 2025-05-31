🛒 Superstore Sales Analysis Dashboard – Power BI
This project presents an end-to-end Business Intelligence (BI) solution using the Superstore Sales Dataset. It includes data modeling using Star Schema, advanced DAX calculations, and interactive Power BI visualizations across multiple report pages. This dashboard provides valuable insights into sales, profit, product performance, and regional trends to assist decision-making for business stakeholders.

📁 Project Overview
The analysis is performed using the Superstore dataset, which contains information on customer orders, products, regions, and sales metrics.
## Contents

- **Dataset**: [Dataset File](./superstore_data.csv)
- **Power BI File**: [Power BI Report](./Superstore_Sales_Report.pbix)  
- **DAX Measures Documentation**: [DAX Measures Documentation](./DAX_Measures_README.md)  
- **Images**: See the [`images/`](./images) folder for screenshots and the data model diagram  

---

## How to Open the Project

1. Download the repository files.  
2. Open `Superstore_Sales_Report.pbix` in **Power BI Desktop** (latest version recommended).  
3. The Power BI file is connected to the provided dataset file (`superstore_data.csv`).  

---

## Connecting the Dataset

- If the PBIX file does not automatically connect to the dataset:  
  - Go to **Transform Data > Data source settings** in Power BI Desktop.  
  - Edit the permissions and file path to point to the local path of `superstore_data.csv`.  
  - Refresh the data to load the dataset.  

---

## DAX Measures

Detailed DAX measures used in this project are documented in [DAX_Measures_README.md](./DAX_Measures_README.md).

---

The entire process is divided into the following major steps:

1. 🧱 Data Modeling (Star Schema)
Imported the original dataset into Power BI.

Divided it into four dimension tables and one fact table:

DimCustomer – Customer-related information

DimDate – Order and Ship Dates

DimLocation – Country, State, City, Region

DimProduct – Product details

FactOrders – Contains all sales-related measures

Created a Date Dimension table using the CALENDAR DAX function for proper time intelligence.

Established relationships between tables to form a clean Star Schema model.

2. 📊 DAX Measures
Developed multiple key performance metrics in the FactOrders table:

% of Total Sales

Best Selling Category

Cumulative Sales

Profit Margin

Year-over-Year (YoY) Sales

Top Product and Top Region

Total Profit, Total Sales, Total Quantity

📈 Report Pages
1. Sales Performance
Cards: Total Sales, Sales YoY, Cumulative Sales

Line Chart: Year-wise Sales with Trendline

Filter: Quarterly Sales Filter

2. Profitability
Cards: Total Profit, Profit Margin

Pie Chart: Profit by Region

Line Chart: Year-wise Profit

Column Chart: Profit by Category

3. Product & Category Insights
Filters: Segment (Consumer, Corporate, Home Office), Category (Furniture, Office Supplies, Technology)

Table: Top 5 Products

Funnel Chart: Category-wise Sales

Clustered Bar Chart: Sales & Quantity by Category

4. Regional & Segment Analysis
Map: State-wise Sales & Profit

Donut Chart: Segment-wise Sales & Profit

Stacked Column Chart: Sales by Region & Segment

5. Summary Dashboard
Text Box: Project Title & Description

Cards: Total Sales, Total Profit, Profit Margin, Best Selling Category, Top Region

Navigation Buttons: For seamless movement between report pages

🚀 Key Insights
2017 had the highest sales: $0.73M, contributing to a total of $2.3M in sales.

Total Profit: $286.4K with an overall Profit Margin of 12.47%.

The West Region contributes the most to profit in the category of office supplies.

Technology category yielded the highest profit individually.

California leads in both sales and profit state-wise.

The Consumer Segment in the West Region shows the most sales and profit.

🧭 Navigation & UX Features
A navigation bar at the top allows easy switching between pages.

Buttons with page actions on the Summary Dashboard for intuitive navigation.

📌 Tools & Technologies
Power BI

DAX (Data Analysis Expressions)

Data Modeling (Star Schema)

Interactive Visuals & UX design

📁 Dataset
The Superstore dataset includes fields like:
Row ID, Order ID, Order Date, Ship Date, Ship Mode, Customer Name, Segment, Country, City, State, Postal Code, Region, Product ID, Category, Sub-Category, Product Name, Sales, Quantity, Discount, Profit

📸 Screenshots
Sales Performance Report  
[Sales Performance](images/sales_performance.png)
Profitability Report  
[Profitability](images/profitability.png)
Product & Category Insights  
[Product & Category](images/product_insights.png)
Regional & Segment Analysis  
[Regional & Segment](images/region_segment.png)
Summary Dashboard  
[Summary Dashboard](images/summary_dashboard.png)

🔗 Project Purpose
This project demonstrates core skills in:

Data Modeling

Advanced DAX Calculations

Storytelling through Data

Professional Dashboard Design

User-Friendly Report Navigation

Feel free to explore the report pages and visuals for deep insights into Superstore sales data.
🙋‍♀️ Author
Muthyala Chaitrika – Aspiring Data Analyst
📫 Feel free to connect with me on [LinkedIn](https://www.linkedin.com/in/chaitrikamuthyala/).


