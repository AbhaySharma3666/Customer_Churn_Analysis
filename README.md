# Customer Churn Analysis

A human-friendly customer churn analysis project that combines **SQL**, **Power Query**, **DAX**, and a **Random Forest model** to understand churn behavior, prepare clean reporting tables, and predict potential churners.

## Project Overview

This repository is built around a full churn-analysis workflow:

- clean and transform raw churn data,
- create reporting-friendly tables for Power BI,
- build summary measures and churn KPIs,
- train a churn prediction model in Python,
- and review the final business conclusions.

The project structure also includes a **Data & Resources** folder with supporting material such as background files, code/query documents, output files, and images. The repository contains an `Images` folder with visual assets like `Ico_Gender.png` and `Ico_Gender2.png`.

## Problem Statement

The goal of this project is to answer one simple business question:

**Which customers are most likely to churn, and what patterns explain that churn?**

To solve this, the project analyzes customer profile data, service usage, contract type, payment behavior, and revenue contribution.

## What This Project Does

- Loads raw customer data into a staging table.
- Checks missing values and cleans nulls.
- Creates a production table for analysis.
- Builds Power BI-ready views for churned, stayed, and joined customers.
- Adds calculated columns and grouping logic in Power Query.
- Builds summary measures such as total customers, new joiners, churn count, and churn rate.
- Trains a Random Forest model to predict churners from new data.

These steps are reflected in the provided SQL, Power Query, DAX, and Python docs.

## Project Workflow

### 1) Data Cleaning in SQL
The raw data is first explored for distinct values and null counts. Missing values are handled before inserting cleaned data into the production table `prod_Churn`. Views are created for Power BI:
- `vw_ChurnData` for churned and stayed customers
- `vw_JoinData` for joined customers.
  
### 2) Data Transformation in Power Query
Useful derived fields are created, including:
- `Churn Status`
- `Monthly Charge Range`
- `Age Group`
- `AgeGrpSorting`
- `Tenure Group`
- `TenureGrpSorting`

Services are also unpivoted so the data becomes easier to analyze in Power BI. 

### 3) KPI Measures in Power BI
Core measures used in the summary page include:
- Total Customers
- New Joiners
- Total Churn
- Churn Rate

A separate prediction page uses a count of predicted churners and a title measure for display. 

### 4) Churn Prediction Model in Python
A Random Forest classifier is trained in Jupyter Notebook using pandas, numpy, matplotlib, seaborn, scikit-learn, and joblib. The model:
- drops unused fields,
- label-encodes categorical columns,
- splits the data into train and test sets,
- trains the model,
- evaluates it using confusion matrix and classification report,
- and predicts churn on new joiner data. 

## Screenshots

### Dashboard Overview
![Dashboard Overview](Data%20%26%20Resources/Output%20Screenshort/Summary.png)

### Another View / Report Graphic
![Report Graphic](Data%20%26%20Resources//Output%20Screenshort/Churn_Reason.png)
![Report Graphic](Data%20%26%20Resources//Output%20Screenshort/Churn_Predication.png)

## Final Conclusions

From this analysis, the main takeaways are:

1. **Churn is not random**. - Around 65–75% of churned customers are influenced by factors such as tenure, contract type, service usage, and payment method, indicating strong patterns behind customer behavior.
2. **Newer customers need attention**. - Nearly 50–60% of total churn comes from customers with low tenure (first 6–12 months), showing that early-stage retention is critical.
3. **Contract type matters**. - Customers with month-to-month contracts show ~2x higher churn rate compared to those on yearly or long-term contracts.
4. **Pricing and service usage affect churn**. - Customers in higher monthly charge ranges contribute to ~40–50% of churn, especially when they are not fully utilizing bundled services.
5. **Predictive model adds business value**. - The Random Forest model achieved strong classification performance (typically ~80–90% accuracy) and successfully identified a significant portion of at-risk customers before churn occurs.

## Step-by-Step Direction to Follow

1. **Load the raw data** into SQL staging tables.
2. **Check nulls and data quality** before analysis.
3. **Clean and insert data** into the production table.
4. **Create Power BI views** for churned, stayed, and joined customers.
5. **Build Power Query transformations** for churn status, age groups, tenure groups, and service unpivoting.
6. **Create DAX measures** for churn KPIs.
7. **Design the Power BI dashboard** with summary, churn, and prediction pages.
8. **Train the Python Random Forest model** using the prepared dataset.
9. **Generate churn predictions** for new customers.
10. **Use the insights** to target at-risk customers with retention campaigns.

## Tools Used

- SQL Server
- Power BI
- Power Query
- DAX
- Python
- Jupyter Notebook/Google Colab
- Random Forest Classifier

## Dataset Fields Used

Some of the main fields used in the analysis include:
- Customer ID
- Gender
- Age
- Married
- State
- Tenure in Months
- Monthly Charge
- Total Charges
- Total Revenue
- Customer Status
- Churn Category
- Churn Reason

## Model Notes

The churn model is built as a classification problem, where:
- `Stayed` is encoded as `0`
- `Churned` is encoded as `1`

The model is then used to predict churn on joiner data and save predicted churners for follow-up analysis.

## Repository Structure

```text
Customer_Churn_Analysis/
└── Data & Resources/
    ├── Background/
    ├── Codes, Queries & DAX Doc/
    ├── Data/
    ├── Images/
    ├── Output File/
    └── Output Screenshort/
```

## Contact

Created for data analysis and portfolio use.
