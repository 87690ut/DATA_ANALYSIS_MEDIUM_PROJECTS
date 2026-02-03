# E-commerce Customer Segmentation (RFM Analysis)

## Project Overview
This project involves analyzing a dataset of over 500,000 online retail transactions to perform Customer Segmentation using the RFM (Recency, Frequency, Monetary) technique. The goal was to identify distinct customer groups (Champions, Loyal, At-Risk) to help businesses optimize marketing strategies.

This project was more than just data analysis—it was a deep dive into Python logic, debugging, and understanding how data actually behaves.

---

## The Real Struggle: Why I spent 5 hours on 1 line of code!
Real learning doesn't happen when the code runs perfectly on the first try. It happens when you hit an error and refuse to give up. I spent 5 hours debugging, facing 3 major challenges that taught me more than any tutorial could:

### 1. The "Always 1" Frequency Trap
- **The Problem:** I was grouping by CustomerID but counting unique CustomerIDs. The result? Everyone's frequency was '1'.
- **The Fix:** Realized that I needed to group by the Person, but count the Invoices.
- **Lesson:** Logic > Syntax. Always question what you are counting.

### 2. The Timedelta Confusion
- **The Problem:** Encountered persistent AttributeErrors while calculating Recency.
- **The Fix:** Dove deep into the datetime library structure to understand how imports and time differences work under the hood.

### 3. The "Not Callable" Bracket Battle () vs []
- **The Problem:** A simple syntax mistake between parentheses and square brackets kept throwing errors.
- **Lesson:** Learned the fundamental difference between calling a function () and selecting data [].

> My biggest takeaway? In Data Analytics, don't just "Copy-Paste." Ask "Why?" until the logic clicks.

---

## Technical Workflow

### 1. Data Cleaning
- **Missing Values:** Dropped rows with null CustomerID (cannot analyze unidentified customers).
- **Data Integrity:** Filtered out negative Quantity values (Product Returns) to focus purely on sales.

### 2. Feature Engineering
- **Total Price:** Calculated Revenue per transaction (Quantity * UnitPrice).
- **Date Conversion:** Converted InvoiceDate to proper datetime objects for time-series calculation.

### 3. RFM Calculation (The Logic)
I grouped the data by CustomerID to calculate:
- **Recency (R):** Days since the last purchase.
- **Frequency (F):** Total number of invoices (transactions).
- **Monetary (M):** Total money spent.

### 4. Scoring & Segmentation
- Used pd.qcut to divide customers into quartiles (1-4).
- Created a custom RFM_Score (e.g., "444", "112").
- **Segmented Customers into:**
  - **VIP/Champions:** (Score 444) - Buy recently, often, and spend the most.
  - **Loyal Customers:** High Frequency scores.
  - **Big Spenders:** High Monetary scores.
  - **Hibernating:** (Score 111) - Haven't visited in a long time.

---

## Visualizations
(Please check the project folder for generated graphs)

- **Customer Distribution:** Visualized how many customers fall into each category (VIP vs. Regular).
- **Revenue Impact:** Analyzed which segment contributes the most to total revenue.

[Bar chart of rfm analysis](Screenshot%202026-02-03%20214522.png)

---

## Business Recommendations
Based on the data, here is the strategy for the business:
1. **For VIPs:** Provide exclusive early access and loyalty rewards.
2. **For Big Spenders:** Recommend higher-margin products (Upselling).
3. **For Lost Customers:** Launch aggressive discount campaigns to re-engage them.

---
Project executed by an Aspiring Data Analyst.