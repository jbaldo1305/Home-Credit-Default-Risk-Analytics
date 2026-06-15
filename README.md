# Home Credit Default Risk Analytics

## Project Overview

This project analyzes loan application data from Home Credit to identify factors associated with loan default risk. The goal is to understand borrower characteristics, credit history, and prior application behavior that may contribute to higher default rates.

The project combines exploratory data analysis, relational data aggregation, Tableau dashboarding, and predictive modeling.

## Business Problem

Financial institutions need to identify applicants with higher default risk before approving loans. Since only about 8% of applicants defaulted, accuracy alone is not a reliable metric. This project focuses on identifying risk patterns and evaluating models using recall, precision, F1-score, and ROC-AUC.

## Dataset

This project uses the Home Credit Default Risk dataset from Kaggle.

Full dataset: https://www.kaggle.com/competitions/home-credit-default-risk

Due to GitHub file size limits, the full raw dataset and Tableau export file are not included. A sample Tableau dataset is included for reference.

## Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Tableau
- Jupyter Notebook

## Data Sources Used

The analysis used multiple related datasets:

- `application_train.csv` — main loan applicant data
- `bureau.csv` — external credit bureau history
- `previous_application.csv` — prior Home Credit application history

These tables were joined using `SK_ID_CURR` to create borrower-level credit history features.

## Key Analysis Steps

1. Loaded and inspected multiple Home Credit datasets
2. Analyzed the target variable and class imbalance
3. Explored default risk by education, income, family status, age, employment length, occupation, and annuity burden
4. Aggregated bureau and previous application tables to create customer-level risk features
5. Built a Tableau dashboard to visualize default risk patterns
6. Trained Logistic Regression and Random Forest models using balanced class weights
7. Compared models using recall, precision, F1-score, confusion matrices, and ROC-AUC

## Key Findings

- The overall default rate was approximately 8.1%.
- Applicants with shorter employment histories had higher default rates.
- Lower education levels were associated with increased default risk.
- Higher annuity-to-income burden was linked to higher default rates.
- Occupation type showed meaningful variation in borrower risk.
- External credit history and previous application behavior provided additional risk signals.

## Tableau Dashboard

An interactive Tableau dashboard was created to visualize borrower risk patterns across employment length, education, income, occupation, and annuity burden.

Dashboard link: PASTE YOUR TABLEAU PUBLIC LINK HERE

![Tableau Dashboard](images/dashboard.png)

## Modeling Results

Two models were evaluated:

| Metric | Logistic Regression | Random Forest |
|---|---:|---:|
| Recall (Default) | 0.61 | 0.00 |
| Precision (Default) | 0.12 | 0.50 |
| F1-Score (Default) | 0.20 | 0.00 |
| ROC-AUC | 0.650 | 0.643 |

Although Random Forest achieved higher overall accuracy, it failed to identify defaulting applicants. Logistic Regression was selected as the better screening model because it achieved substantially higher recall for the default class.

## Business Recommendation

The Logistic Regression model may be useful as an initial credit-risk screening tool because it identifies a larger portion of potential defaults. However, due to low precision, the model should not be used as the sole decision-making tool. Instead, it should support further review by risk analysts.

## Limitations

- The dataset is highly imbalanced, with default cases representing only about 8% of applicants.
- Some columns contained substantial missing values.
- The model used selected engineered features and did not include every available variable.
- The Random Forest model struggled to detect default cases despite class weighting.

## Future Improvements

- Add more engineered features from additional Home Credit tables
- Tune model hyperparameters
- Test gradient boosting models such as XGBoost or LightGBM
- Improve threshold tuning to balance recall and precision
- Expand Tableau dashboard with additional credit bureau metrics
