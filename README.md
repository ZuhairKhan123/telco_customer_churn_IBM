**Telco Customer Churn & LTV Engine**
A data science project built on the IBM Telco dataset (7,032 customers) that combines Python-based feature engineering with a Power BI dashboard to identify at-risk customers and quantify revenue exposure.

**What it does**
Segments customers into High / Medium / Low churn risk
Calculates Customer Lifetime Value (CLTV) and Net Retention Value
Flags revenue at risk from high-churn segments
Lets you explore everything interactively through slicers, conditional formatting, and a map visual

telco-customer-churn-IBM/

├── data/
│   ├── Customer-Churn.xlsx
│   └── processed/customer_churn_phase3_prep.xlsx
├── notebooks/
│   ├── RFM_Customer_Chern.ipynb    # EDA, RFM scoring, CLTV
│   └── ML_Customer_Churn.ipynb     # Churn probability model
├── powerbi/
│   └── Phase5_Dashboard.pbix
└── README.md

**Stack**
LayerToolsData ProcessingPython, Pandas, NumPyMachine LearningScikit-learnDatabaseSQL Server Express (Azure Data Studio)VisualizationPower BI Desktop

**Engineered Features**
Churn Probability
CLTV
Net Retention Value
Discount Rate Value
Risk Label
RFM Score

**ML Models Used**
Logistic Regression
XGBoost
