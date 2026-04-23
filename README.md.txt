An interactive Power BI dashboard analyzing customer churn patterns for a Telecom company. Built as part of the **BI Reporting with Power BI** certification course.

---

## 🎯 Project Objective

A telecom company is losing customers and wants to understand **who is churning, why, and how much revenue is being lost**. This dashboard provides an executive-level view of churn patterns across contract types, services, and customer demographics.

---

## 🗂️ Dataset

| Property | Details |
|---|---|
| **Source** | [Telco Customer Churn — Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) |
| **Rows** | 7,043 customers |
| **Target Variable** | `Churn` (Yes / No) |
| **Key Features** | Contract, MonthlyCharges, tenure, InternetService, PaymentMethod, gender |

---

## 🧰 Tools & Technologies

| Tool | Usage |
|---|---|
| **Power BI Desktop** | Dashboard development |
| **Power Query** | Data transformation & cleaning |
| **DAX** | Calculated measures & KPIs |
| **Python (in Power BI)** | Violin plot visualization |

---

## ⚙️ Data Transformation (Power Query)

- Fixed `TotalCharges` column from Text → Decimal Number
- Removed errors from `TotalCharges` column
- Added custom `ChurnFlag` column:
  ```
  = if [Churn] = "Yes" then 1 else 0
  ```
- Changed `ChurnFlag` data type to Whole Number

---

## 📐 DAX Measures

All measures are stored in a dedicated `_Measures` table (best practice):

```dax
Total Customers = COUNTROWS('WA_Fn-UseC_-Telco-Customer-Churn')

Total Churned = SUM('WA_Fn-UseC_-Telco-Customer-Churn'[ChurnFlag])

Churn Rate = DIVIDE([Total Churned], [Total Customers], 0)

Revenue Lost = 
CALCULATE(
    SUM('WA_Fn-UseC_-Telco-Customer-Churn'[MonthlyCharges]),
    'WA_Fn-UseC_-Telco-Customer-Churn'[Churn] = "Yes"
)
```

---

## 📊 Dashboard Components

| Visual | Type | Insight |
|---|---|---|
| Total Customers | KPI Card | Overall customer base size |
| Total Churned | KPI Card | Number of lost customers |
| Churn Rate | KPI Card | % of customers who left |
| Revenue Lost | KPI Card | Monthly revenue impact of churn |
| Churn Split | Donut Chart | Overall Yes vs No churn ratio |
| Churn Rate by Contract | Bar Chart | Which contract types drive churn |
| Segment Summary | Matrix + Conditional Formatting | Churn rate heatmap by segment |
| What Drives Churn? | Decomposition Tree (AI Visual) | Interactive drill-down into churn factors |
| Contract Slicer | Dropdown Slicer | Filter entire dashboard by contract |
| Gender Slicer | Tile Slicer | Filter entire dashboard by gender |

---

## 📸 Dashboard Preview

![Dashboard](dashboard_screenshot.png)

---

## 🔑 Key Insights

1. **~26.5% overall churn rate** — significantly above the 15% industry benchmark
2. **Month-to-month contracts** have ~42% churn rate vs ~3% for two-year contracts
3. **Fiber optic customers** churn the most despite paying the highest monthly charges
4. **~$139K/month** in revenue is being lost to churned customers
5. **Electronic check** payment users churn more than auto-payment users
6. Customers in their **first 12 months** are the highest risk group

---

## 📁 Project Structure

```
customer-churn-powerbi/
│
├── CustomerChurnDashboard.pbix     ← Power BI file (main deliverable)
├── README.md                       ← Project documentation
└── dashboard_screenshot.png        ← Dashboard preview image
```

> ⚠️ Dataset not included due to size. Download from [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn).

---

## 🔗 Course Concepts Demonstrated

| Course Module | Applied In Project |
|---|---|
| Data Transformation — Query Editor | TotalCharges fix, ChurnFlag column |
| Data Transformation — Advanced | Data type corrections, error removal |
| Creating a Data Model | _Measures table, structured DAX |
| DAX Essentials | COUNTROWS, SUM, DIVIDE, CALCULATE |
| Key Measure Table | All measures in dedicated _Measures table |
| Data Visualization | Cards, Donut, Bar, Matrix, Decomposition Tree |
| Conditional Formatting | Color scale on Matrix churn rate column |
| Filter Visual / Slicers | Contract dropdown + Gender tile slicer |
| Decomposition Tree | AI-powered churn driver drill-down |
| Tell a Story with Data | KPI-first layout, natural reading pattern |

---

## 👤 Author

**Your Name**  
B.Sc. / B.Tech — Data Science  
GitHub: [@yourusername](https://github.com/yourusername)

---

## 📄 License

This project is for educational purposes as part of a Data Science course and BI Reporting certification portfolio.