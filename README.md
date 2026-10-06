# Banking Customer Churn Prediction

<a href="https://colab.research.google.com/github/CamilaTovarm/banking-customer-churn-prediction/blob/main/ProyectoNCK.ipynb" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

This repository contains an end-to-end machine learning project designed to predict customer churn in a banking context using Python in Google Colab. The project combines data extraction from Google BigQuery, data processing, exploratory analysis, feature engineering, model training, evaluation, and deployment of predictions to a BigQuery table for downstream reporting and business decision-making.

## Project Overview

Customer churn is one of the most important indicators for banks and financial institutions because it directly affects revenue, customer retention, and long-term profitability. This project focuses on identifying customers at high risk of leaving the bank by analyzing behavioral, financial, and demographic signals.

The workflow includes:

- Data extraction from BigQuery
- Data cleaning and preprocessing
- Exploratory data analysis (EDA)
- Feature engineering and transformation
- Training multiple machine learning models
- Model comparison and selection
- Risk scoring for each customer
- Prediction export back to BigQuery
- Customer segmentation by churn risk level

## Business Objective

The main goal is to help the business act proactively by detecting churn risk early and identifying the customers that may require retention strategies, personalized offers, or customer success interventions.

This solution is useful for:

- Retention campaigns
- Customer segmentation
- Identifying high-risk profiles
- Supporting business and marketing teams
- Reducing churn and improving customer lifetime value

## Dataset and Data Model

The project uses a banking customer dataset that combines customer information and transaction/activity data. The data includes variables such as:

- Customer ID
- Geography / country
- Gender
- Age
- Credit score
- Balance
- Estimated salary
- Tenure
- Number of products
- Account activity status
- Churn target: Exited
- Additional features such as customer type, activity date, registration date, and recency indicators

The dataset was loaded from BigQuery and consolidated into a final table named `TablaFinal`, which was later used for training and inference.

## Key Features of the Project

- Google Colab friendly environment for Python experimentation
- BigQuery integration for cloud data access
- Structured data preparation and merging across tables
- Churn target analysis and class distribution checking
- EDA using `pandas`, `matplotlib`, and `seaborn`
- Feature engineering for risk analysis
- Multiple ML models trained and compared
- Hyperparameter tuning using `GridSearchCV`
- Model persistence with `pickle`
- Batch predictions exported to BigQuery
- Risk summaries and customer-level targeting

## Technologies Used

### Programming and Data Science
- Python
- Jupyter Notebook / Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost

### Cloud and Data Storage
- Google Cloud Platform (GCP)
- Google BigQuery
- Google Authentication / Service Account credentials

### Machine Learning
- Logistic Regression
- Random Forest Classifier
- XGBoost Classifier
- Train/test splitting
- Stratified validation
- Confusion matrix
- ROC curves
- Precision, Recall, F1 Score, Accuracy

### Model Engineering and Export
- `pickle` for model serialization
- StandardScaler for preprocessing
- Batch prediction export to BigQuery
- Risk categorization for customer prioritization

## Project Workflow

1. Connect to BigQuery using service account credentials.
2. Load customer and transactional data from the warehouse.
3. Merge and clean data to build a single customer dataset.
4. Explore variables and detect patterns related to churn behavior.
5. Engineer additional variables such as recency, activity duration, customer profile, and score categories.
6. Prepare inputs for machine learning.
7. Train several candidate models:
   - Logistic Regression
   - Random Forest
   - XGBoost
8. Compare model performance using classification metrics.
9. Select the best-performing model.
10. Tune the selected model using cross-validation and grid search.
11. Save the trained model and scaler.
12. Generate churn risk probabilities for all customers.
13. Upload results to BigQuery.
14. Expose a risk-based customer view for business reporting.

## Model Evaluation Strategy

The project evaluates the models using standard binary classification metrics, including:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix

The notebook compares multiple models to identify the best-performing algorithm for churn prediction. The best-performing model in this workflow was XGBoost, which showed strong predictive power in identifying customers likely to churn.

## Churn Risk Output

The model generates predictions including:

- `customer_id`
- `churn_real`
- `churn_predicho`
- `probabilidad_churn`
- `riesgo_categoria`
- `es_alto_riesgo`
- `requiere_atencion`

These fields are stored in BigQuery tables and used to prioritize retention actions.

## How to Run This Project in Google Colab

1. Open the notebook in Google Colab using the badge above.
2. Upload or connect the required Google Cloud service account JSON file.
3. Install the required dependencies if needed:

```python
!pip install --upgrade google-cloud-bigquery google-cloud-storage pandas pyarrow db-dtypes
```

4. Configure your project ID and BigQuery dataset/table names.
5. Execute the notebook cells sequentially.
6. Review the EDA, model metrics, and outputs.
7. Validate that predictions are saved back to BigQuery.

## Example of the Main Workflow

```python
from google.cloud import bigquery
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from xgboost import XGBClassifier
```

## Important Notes

- The project is designed for execution in the Google Colab environment.
- BigQuery credentials are required to run the notebook successfully.
- The dataset should be well structured and cleaned before modeling.
- Churn prediction models should be monitored and updated regularly as the customer base changes.
- This project is not only a technical exercise but also a practical decision-support tool for customer retention.

## Expected Business Impact

This project can generate value by:

- Increasing retention of high-risk customers
- Reducing the cost of reactive customer acquisition
- Improving marketing efficiency
- Supporting strategic business decisions with data-driven insights
- Creating an analytical foundation for future AI and retention workflows

## Future Improvements

Possible enhancements include:

- Hyperparameter tuning for more advanced models
- Synthetic oversampling for class imbalance handling
- Time-based churn prediction using customer lifecycle analysis
- Dashboarding in Power BI or Looker Studio
- Real-time scoring and automated alerts for at-risk customers
- Integration with CRM or customer engagement systems

## Conclusion

This project demonstrates how Python, machine learning, and BigQuery can be combined to build an effective banking customer churn prediction system in Google Colab. It combines modern data engineering, practical analytics, and predictive modeling to deliver business value in a highly relevant domain.
