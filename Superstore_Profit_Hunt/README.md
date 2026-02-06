# 🛒 Superstore Sales & Profit Analysis

### 🚀 Analyzing Profitability Issues in Retail using Python
**Goal:** To diagnose why the company is facing profit losses in specific areas despite high sales volume, and to identify seasonal sales trends.

---

## 📌 Business Problem
The Superstore Giant has been generating consistent sales, but the stakeholders noticed that **Profit margins are not growing** proportionately.
They hired me to answer two critical questions:
1.  **Where are we losing money?** (Which products/categories are bleeding cash?)
2.  **When do we sell the most?** (Seasonal trends for inventory planning).

---

## 🛠️ Data Cleaning & Pre-processing (The Real Challenge)
Raw data is never perfect. Before analyzing, I had to fix critical data quality issues that were crashing the code.

### 1. Handling Inconsistent Dates 🗓️
* **Challenge:** The `Order Date` column was a mess! It contained mixed separators (both `/` and `-`), causing standard conversion to fail.
* **Solution:**
    * **Normalization:** Standardized the format by replacing all slashes (`/`) with hyphens (`-`).
    * **Parsing:** Used `pd.to_datetime()` with `dayfirst=True` to correctly interpret the Day-Month-Year format.
    * **Safety:** Applied `errors='coerce'` to handle garbage values without breaking the pipeline.

### 2. Cleaning Numerical Data (Sales Column) 💰
* **Challenge:** The `Sales` column was treated as "Text" (Object) by Python because it contained commas (e.g., `1,648`) and hidden whitespace.
* **Solution:**
    * **Sanitization:** Removed commas using `.str.replace(',', '')`.
    * **Conversion:** Cast the column to `float` to enable mathematical aggregations like Sum and Mean.

### 3. Feature Engineering (Time Travel) ⏳
* **Objective:** To analyze monthly seasonality, raw dates were not enough.
* **Implementation:** Extracted **Month Name** (e.g., January, September) and **Year** into new columns using `.dt.month_name()`. This allowed for clear trend visualization.

---

## 📊 Key Insights & Visuals

### 1. Sales Seasonality (When do people buy?)
* **Observation:** The company sees a massive surge in sales during **November and December**.
* **Reason:** Likely due to end-of-year festivals and holidays.
* **Low Point:** **February** is the slowest month for the business.


![Sales by month chart](Screenshot%202026-02-06%20104757.png)

### 2. The "Furniture" Trap (Profit vs Sales)
* **Observation:** While **Technology** generates high sales AND high profit, **Furniture** has a serious problem. It has decent sales volume but extremely low profit margins compared to other categories.


![Profit by category image](Screenshot%202026-02-06%20104856.png)

---

## 📉 The Culprit Found: "Tables"
Upon drilling down into the Furniture category, I discovered the root cause of the profit leak.
* **Sub-Category Analysis:** While Chairs and Bookcases are profitable, **Tables** are running in a **Negative Profit (Loss)**.
* **Impact:** The heavy losses from Tables are eating up the profits earned by other furniture items.


![Sub category of furniture by profit image](Screenshot%202026-02-06%20105941.png)

---

## 💡 Business Recommendations
Based on the data, I recommend the following actions to the stakeholders:
1.  **Investigate "Tables":** Stop offering high discounts on Tables immediately. Check shipping costs (Tables are heavy) to see if logistics is killing the margin.
2.  **Inventory Planning:** Stock up heavily in **October** to prepare for the November-December rush.
3.  **Marketing:** Run promotional campaigns in **February** to boost sales during the slow period.

---
*Analyzed by [Uttam Tiwari] - Python Data Analytics*