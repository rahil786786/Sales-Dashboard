# Interactive Sales Performance Dashboard using Tableau

### Project Author: Rahil Ahmed Shaikh

## 📜 Project Introduction

This repository contains the source files for an interactive Sales Performance Dashboard created with Tableau. The primary goal of this project is to provide a dynamic and insightful tool for analyzing sales data, aimed at helping business stakeholders make informed, data-driven decisions.

The dashboard addresses a common business challenge: the need to quickly understand complex sales data, track performance against historical benchmarks, and identify key drivers of profitability without manual data processing.

### 🔑 Key Business Questions Answered:
* What are the total sales, profit, and quantity sold for a given period?
* How does our performance this year compare to the previous year?
* Which are our highest and lowest performing months?
* Which product subcategories are the most profitable versus those that are just high-volume?
* How do sales and profit fluctuate on a weekly basis, and which weeks are outperforming the average?

---

## 📊 Dashboard Preview

*(Suggestion: Record a short GIF of you clicking through the filters and add it here for a live demo! You can replace the image link below.)*

![Sales Dashboard Preview](https://i.imgur.com/your-dashboard-image.png)

---

## 🎯 Interactive Features & Technical Deep Dive

#### 1. KPI Overview Cards
* **Feature:** Displays high-level metrics for Total Sales, Profit, and Quantity.
* **Technical Implementation:** KPIs are supplemented with a Year-over-Year (YoY) percentage change, calculated using Tableau's **Percent Difference From** Table Calculation computed across the 'Year' dimension.

#### 2. Monthly Sales & Profit Trends
* **Feature:** A dual-axis line chart compares current year and previous year performance month-over-month.
* **Technical Implementation:** Utilizes a dual-axis chart to overlay two measures. A calculated field using **WINDOW_MAX()** and **WINDOW_MIN()** is used to conditionally color the highest and lowest points on the chart for immediate visual emphasis.

#### 3. Sales & Profitability by Subcategory
* **Feature:** A combination chart shows total sales (bar chart) and profit (color-coded) for each product subcategory.
* **Technical Implementation:** A simple bar chart where the `SUM(Sales)` determines the length and a calculated field for Profit (`SUM(Profit) > 0`) is dropped onto the Color mark to instantly distinguish profitable from non-profitable categories.

#### 4. Weekly Performance vs. Average
* **Feature:** Tracks weekly sales and profit, highlighting weeks that perform above or below the overall average.
* **Technical Implementation:** Achieved using a **Reference Line** set to the average of the view. A calculated field like `IF SUM([Sales]) > WINDOW_AVG(SUM([Sales])) THEN 'Above' ELSE 'Below' END` is used on the Color mark to shade the bars accordingly.

#### 5. Dynamic Filtering
* **Feature:** The entire dashboard can be filtered by Year and Location (Region/State/City).
* **Technical Implementation:** Global filters are applied to all relevant worksheets on the dashboard, allowing users to drill down into the data and explore insights for specific segments.

---

## 🛠️ Tools and Technologies

* **Visualization Tool:** Tableau Desktop
* **Data Source:** Sample - Superstore Dataset (Transactional retail data)
* **Core Concepts Applied:**
    * Data Modeling & Relationships
    * Calculated Fields & Table Calculations
    * Level of Detail (LOD) Expressions
    * Dashboard Actions and Interactive Filters
    * Reference Lines and Conditional Formatting

---

## 💡 Potential Future Improvements

* **Forecasting:** Integrate Tableau's forecasting models to predict sales for the next quarter.
* **Parameter Actions:** Add parameters to allow the user to dynamically switch the measures shown in the trend charts (e.g., from Sales to Quantity).
* **Customer Analysis:** Add a new dashboard page focusing on customer segmentation using RFM (Recency, Frequency, Monetary) analysis.

---

## 🚀 How to Use

1.  Clone this repository to your local machine.
2.  Open the `.twbx` (Tableau Packaged Workbook) file in Tableau Desktop or Tableau Reader.
3.  Interact with the filters and visuals to explore the data insights!
