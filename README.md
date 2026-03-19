# 📡 Telco Customer Churn & LTV Engine

> A full-stack data science project combining Python-based feature engineering with an interactive Power BI dashboard to identify at-risk customers, quantify revenue exposure, and support data-driven retention decisions.

---

## 📊 Live Dashboard Preview

![Telco Customer Churn Dashboard](Link: https://app.powerbi.com/groups/me/reports/86bd8f28-2df8-4667-9ff1-89204d7726c0/7ef2200b94041b40a59d?experience=power-bi)

> *Built in Power BI using the IBM Telco Customer Churn Dataset (7,032 customers)*

---

## 🧠 Project Overview

Customer churn is one of the most costly problems in the telecom industry. This project builds an end-to-end **Churn & Lifetime Value (LTV) Engine** that:

- Segments customers by **churn risk** (High / Medium / Low)
- Calculates **Customer Lifetime Value (CLTV)** and **Net Retention Value**
- Quantifies **Revenue at Risk** from high-churn customers
- Visualizes everything in an **interactive Power BI dashboard** with slicers, conditional formatting, and geographic mapping

---

## 🗂️ Project Structure

```
telco-churn-ltv-engine/
│
├── data/
│   ├── WA_Fn-UseC_-Telco-Customer-Churn.xlsx   # Raw IBM Telco dataset
│   └── processed/
│       └── customer_churn_phase3_prep.xlsx                  # Engineered feature set
│
├── notebooks/
│   ├── RFM_Customer_Chern.ipynb           # Exploratory Data Analysis | RFM + CLTV calculations
│   ├── ML_Customer_Churn.ipynb            # Churn probability model
│   
│
├── powerbi/
│   └── Phase5_Dashboard.pbix                   # Power BI dashboard file
└── README.md
```

---

## 🔧 Tech Stack

| Layer | Tools |
|---|---|
| **Data Processing** | Python, Pandas, NumPy |
| **Machine Learning** | Scikit-learn |
| **Database** | SQL Server Express (Azure Data Studio) |
| **Visualization** | Power BI Desktop |
| **Dataset** | IBM Telco Customer Churn (Kaggle) |

---

## 📐 Feature Engineering

The following features were engineered from the raw dataset using Python:

| Feature | Description |
|---|---|
| `Churn Probability` | Predicted churn likelihood (0–1) using logistic regression |
| `CLTV` | Customer Lifetime Value = `(Monthly Charges × Tenure) × (1 - Churn Probability)` |
| `Net Retention Value` | Revenue retained after accounting for churn risk |
| `Discount Rate Value` | Applied discount cost per customer for retention campaigns |
| `Risk Label` | Segmentation into High / Medium / Low churn risk |
| `RFM Score` | Recency, Frequency, Monetary scoring |

---

## 📈 Key DAX Measures (Power BI)

```dax
-- Total Customers
Total Customers = COUNTROWS('Sheet1')

-- High Risk Count
High Risk Count = 
CALCULATE(
    COUNTROWS('Sheet1'),
    'Sheet1'[Risk Label] = "High Risk"
)

-- Revenue At Risk
Revenue At Risk = 
CALCULATE(
    SUM('Sheet1'[Monthly Charges]),
    'Sheet1'[Risk Label] = "High Risk"
)

-- Average CLTV
Average CLTV = AVERAGE('Sheet1'[CLTV])

-- CLTV Exceeded Flag (Conditional Formatting)
CLTV Exceeded Flag = 
IF(
    SELECTEDVALUE('Sheet1'[Discount Rate Value]) > SELECTEDVALUE('Sheet1'[CLTV]),
    "#E81123",
    "#FFFFFF"
)
```

---

## 🎨 Dashboard Features

### KPI Cards
- **2K** High Risk Customers
- **$1.02M** Revenue at Risk
- **$542.76** Average CLTV
- **$3.36M** Net Retention Value

### Visuals
| Visual | Description |
|---|---|
| Bar Chart | Customers by Risk Label (Red / Yellow / Green) |
| Scatter Plot | Churn Probability vs CLTV |
| Pie Chart | Phone Service Breakdown |
| Map | Geographic customer distribution |
| Table | Discount Retention Impact with conditional CLTV formatting |

### Slicers
- Contract Type (Month-to-month / One Year / Two Year)
- Risk Label (High / Medium / Low)
- Tenure Months (range slider)
- Discount Rate (range slider)

---

## 🚀 How to Run

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/telco-churn-ltv-engine.git
cd telco-churn-ltv-engine
```

### 3. Run the Notebooks in Order
```bash
jupyter notebook notebooks/RFM_Customer_Chern.ipynb
jupyter notebook notebooks/ML_Customer_Churn.ipynb
```

### 4. Open the Dashboard
- Open `powerbi/Phase5_Dashboard.pbix` in **Power BI Desktop**
- Refresh the data source to point to your local `data/processed/customer_churn.xlsx`

---

## 📦 Requirements

```
pandas>=1.5.0
numpy>=1.23.0
scikit-learn>=1.2.0
matplotlib>=3.6.0
seaborn>=0.12.0
jupyter>=1.0.0
openpyxl>=3.0.0
```

---

## 📊 Dataset

**IBM Telco Customer Churn Dataset**
- Source: [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- 7,032 customers
- 21 raw features including demographics, services, and churn label
- Target variable: `Churn` (Yes / No)

---

## 💡 Key Insights

- **~28%** of customers are at High churn risk
- High risk customers generate **$1.02M** in monthly revenue exposure
- **Month-to-month** contract holders churn at significantly higher rates
- Customers with **tenure < 12 months** account for the majority of churn
- Discount campaigns only make sense when `Discount Cost < CLTV`

---

## 🔮 Future Improvements

- [ ] Add XGBoost / Random Forest model for improved churn prediction accuracy
- [ ] Build Page 2 in Power BI — Churn Model Performance (confusion matrix, ROC curve)
- [ ] Add Page 3 — Retention Strategy by Segment
- [ ] Connect Python model output live to Power BI via Python visual
- [ ] Deploy as a Streamlit web app for non-technical stakeholders

---

## 👤 Author

**Zuhair Khan**
- 💼 [LinkedIn] (https://www.linkedin.com/in/zuhair-khan-12095116b/)

---

## 🙏 Acknowledgements

- IBM for the Telco Customer Churn dataset
- Microsoft Power BI community for DAX resources
