# **Retail-sales-project-pyspark**

This project is an end-to-end data analysis solution built using **PySpark** on **Databricks**. The goal wasn't just to query data, but to build a reactive workflow that mimics a real world business dashboard. I took the raw "Superstore" retail dataset and built a pipeline that allows stakeholders to track performance metrics dynamically. Instead of static reports, I added widget controls so users can toggle between **Weekly** and **Monthly** views to see how KPIs change over time. 

## 🛠️ Tech Stack
*   **Platform:** Databricks (Community Edition)
*   **Language:** Python (PySpark)
*   **Format:** CSV
*   **Key Concepts:** Dataframes, Spark SQL, Widgets

## 📊 Business Requirements & Features
I structured the analysis to answer specific questions from stakeholders, breaking them down into four main categories:

### 1. The Big Picture (KPIs)
*   Calculated total **Customers**, **Orders**, **Sales**, and **Profit**.
*   These update automatically based on the selected time period (Week vs. Month).

### 2. Geographical Insights
*   **Top Sales by Country:** Identified which countries are driving the most revenue.
*   **Profitability Check:** Drilled down into regions to see which are the most (and least) profitable.

### 3. Product Performance
*   **Category Ranking:** Ranked top-performing categories and sub-categories.
*   **Volume Analysis:** Found the specific products with the highest order quantities.

### 4. Customer Segmentation
*   **Top Customers:** Logic to identify VIP customers based on sales volume and city.

## 💡 Technical Highlights / Challenges
One of the trickier parts of this project was handling the dates.

**Dynamic Filtering:**
I used `dbutils.widgets` to create a dropdown for "Time Period." This passes a variable into the Python logic which recalculates the start and end dates on the fly.

**Handling Historical Data:**
Since the dataset ends in **2024**, simply running `date.today()` (which would be 2025) returned zero results. I implemented logic to simulate "today" relative to the dataset's max date, ensuring the weekly/monthly logic actually filters relevant data instead of returning empty tables.
