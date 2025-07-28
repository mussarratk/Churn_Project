# eCommerce Churn Project in Power BI

# 📊 Customer Churn Analysis Project - Power BI | SQL | Python (EDA)

## 🧠 Project Overview

Customer churn is a critical business metric that directly impacts profitability and long-term sustainability. In this project, I performed a full-stack data analysis using **SQL for data cleaning**, **Python (Jupyter Notebook) for EDA**, and **Power BI** for **data modeling, DAX measures**, and **interactive dashboards**.

The goal was to:
- Identify key factors affecting churn,
- Understand customer behavior,
- Present business insights via a Power BI dashboard,
- Generate actionable recommendations for retention.

## 🛠️ Tools & Technologies Used

| Stack | Details |
|-------|---------|
| **SQL** | MySQL – Data preprocessing, cleaning, transformations |
| **Python** | Jupyter Notebook – Exploratory Data Analysis (EDA), Pandas, NumPy, Matplotlib, Seaborn |
| **Power BI** | Data modeling, DAX Measures, Dashboard Design |
| **Power Query (M)** | Data transformation before modeling in Power BI |
| **DAX (Data Analysis Expressions)** | Custom KPIs, Measures, and calculated columns |

## 🧹 Data Preparation & Cleaning (SQL)

- ✅ **Created Database & Validated Records**
- ✅ Checked for **duplicates and nulls**
- ✅ **Replaced or imputed NULLs** with column averages
- ✅ Created new categorical ranges (TenureRange, CashbackAmountRange, WarehouseToHomeRange)
- ✅ Corrected inconsistent categorical values (e.g., "Mobile Phone" vs. "Phone")
- ✅ Created flags for `CustomerStatus` and `ComplainReceived`

📌 **Sample SQL Operations:**
```sql
-- Handle NULLs
UPDATE ecommercechurn 
SET Tenure = (SELECT AVG(Tenure) FROM ecommercechurn WHERE Tenure IS NOT NULL)
WHERE Tenure IS NULL;

-- Create 'CustomerStatus'
UPDATE ecommercechurn
SET CustomerStatus = CASE WHEN Churn = 1 THEN 'Churned' ELSE 'Stayed' END;
```

## 🔍 Exploratory Data Analysis (Python)

Performed EDA using Seaborn & Matplotlib. Key visualizations included:

- Gender vs Churn
- Satisfaction Score vs Churn
- Complaint vs Churn
- Marital Status vs Churn
- Preferred Device/Order Category vs Churn

📌 **Insights Discovered:**

| Insight | Observation |
|--------|-------------|
| **Gender** | Male customers churn more (10.7%) than females (6.2%) |
| **Complaints** | 9.0% of churned customers have raised complaints |
| **Satisfaction** | Even customers with satisfaction scores of 5 have churned |
| **Marital Status** | Single users show the highest churn (8.5%) |
| **Device** | Customers using mobile phones for login churn more (11.1%) |

## 📦 Power BI Data Modeling

### Power Query (ETL):
- Loaded cleaned data
- Transformed & typed columns
- Created Date table (if time series needed)

### Data Model:
- **Star schema**: `Fact` table for churn data and dimension-like categories
- Relationships built for accurate slicing/filtering

## 📈 Power BI DAX Measures

Below are custom DAX Measures created:

```dax
-- Total Customers
Total Customers = COUNT(ecommercechurn[CustomerID])

-- Churned Customers
Churned Customers = CALCULATE([Total Customers], ecommercechurn[Churn] = 1)

-- Churn Rate %
Churn Rate % = DIVIDE([Churned Customers], [Total Customers], 0)

-- Avg. Hour Spent on App
Avg Hours on App = AVERAGE(ecommercechurn[HourSpendOnApp])

-- Coupon Usage by Churn
Coupon Usage (Churned) = 
CALCULATE(SUM(ecommercechurn[CouponUsed]), ecommercechurn[CustomerStatus] = "Churned")
```

## 📊 Power BI Dashboard Highlights

Interactive dashboard includes:

✅ KPI Cards:
- Total Customers
- Churned Customers
- Churn Rate
- Avg App Usage

✅ Visuals:
- Bar charts on gender, marital status, satisfaction score
- Device & order preferences of churned users
- Distribution of complaints, coupon usage, cashback range

✅ Filters:
- Tenure Range
- City Tier
- Payment Mode
- Complain Status

📌 **Visual Insight Examples:**
- Customers with 0–6 months tenure churn the most (72%)
- Customers from Tier 1 cities show higher churn
- Higher coupon usage correlates with retention
- Complaint handling quality is a significant churn factor

## 🔁 Business Recommendations

1. **Improve First 6 Months Experience**  
   Onboard and engage new users early to prevent early churn.

2. **Target Single Customers with Bundles**  
   Incentivize more purchases by offering combined or bulk deals.

3. **Enhance Mobile App UX**  
   Since churners prefer mobile, enhancing app usability can boost retention.

4. **Respond to Complaints Faster**  
   High churn from complainers suggests poor service recovery.

5. **Optimize Cashback Strategy**  
   Moderate cashback segments show high churn—review reward structures.

6. **Monitor Frequent Device Switching**  
   May indicate trust issues or dissatisfaction with service.

## 🧑‍💼 Role & Skills Demonstrated

✅ **Power BI Analyst & Developer**

| Skill | Description |
|-------|-------------|
| **Data Cleaning (SQL)** | Used SQL queries for profiling, data corrections, and transformations |
| **Exploratory Data Analysis** | Discovered patterns & validated hypotheses using Python |
| **Power Query (M)** | Performed ETL operations in Power BI |
| **DAX Calculations** | Created custom measures and KPIs |
| **Dashboard Design** | Created visually appealing, filter-enabled, insight-rich dashboards |
| **Communication of Insights** | Converted technical analysis into actionable business strategies |

## 📁 Folder Structure

```bash
ecommerce-churn-analysis/
│
├── SQL/
│   └── ecommerce_churn_cleaning.sql
├── Python_EDA/
│   └── churn_eda.ipynb
├── PowerBI/
│   └── ChurnDashboard.pbix
├── Images/
│   └── churn_visuals.png
└── README.md
```

## 📍 Conclusion

This project demonstrates end-to-end skills in:
- SQL Data Engineering
- Python-based EDA
- Power BI Modeling & Dashboards
- Generating business-ready insights

It helped identify churn behaviors and gave the business clear strategies for improving retention.
