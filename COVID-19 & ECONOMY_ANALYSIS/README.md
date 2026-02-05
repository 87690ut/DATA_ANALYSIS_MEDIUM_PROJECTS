# 🌍 Health vs Wealth: Global COVID-19 & Economic Analysis

### 🧐 Does a Country's Wealth Guarantee Better Health Outcomes?
This project explores the relationship between a nation's economy (**GDP per Capita**) and its ability to handle the COVID-19 pandemic (**Death Rates**).

---

## 📊 Project Overview
The common assumption is that wealthier nations with better healthcare infrastructure would have lower death rates during a pandemic. I used Python to test this hypothesis by analyzing real-world data from 80+ countries.

* **Tech Stack:** Python, Pandas, Seaborn, Matplotlib
* **Data Sources:**
    * COVID-19 Dataset (Country-wise latest)
    * World Happiness Report (for GDP Data)

---

## ⚙️ Key Technical Steps

### 1. Data Cleaning & Preprocessing
* Loaded raw datasets and standardized country names to ensure accurate merging.
* Filtered the GDP dataset to retain only the latest economic data (2020-2021).
* Addressed missing values and data inconsistencies.

### 2. Data Merging
* Performed an **Inner Join** (`pd.merge`) to combine health data with economic data.
* Result: A unified dataset connecting COVID statistics directly with GDP figures.

### 3. Feature Engineering
Created new KPIs to normalize the data for fair comparison:
```python
# Calculating Death Rate Percentage
df['Death_Rate'] = (df['Deaths'] / df['Confirmed']) * 100

# Calculating Recovery Rate Percentage
df['Recovery_Rate'] = (df['Recovered'] / df['Confirmed']) * 100

--- Here is Image of the scattered chart of report-


![scattered chart](Screenshot%202026-02-05%20181007.png)
