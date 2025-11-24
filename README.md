# StayWise Airbnb Pricing Prediction

Predicting nightly listing prices using AWS S3, MLflow, and machine learning.

## 1. Project Overview

StayWise is a global vacation rental service aiming to provide hosts with accurate, data-driven pricing recommendations. Nightly prices vary widely across New York City, influenced by neighbourhood, room type, host behavior, and property attributes.

This project builds a complete ML workflow that:

Loads the Airbnb dataset directly from AWS S3

Cleans and preprocesses data

Performs feature engineering

Trains multiple regression models

Tracks all experiments using MLflow

Registers the best-performing model

Generates explainability charts using SHAP

The workflow is fully reproducible and structured for production use.

2. Objectives

Retrieve the Airbnb dataset from AWS S3 using secure programmatic access.

Perform complete data preprocessing, including missing value treatment and outlier handling.

Engineer features to improve predictive power.

Train and compare several regression models.

Use MLflow for experiment tracking, comparison, and model registry.

Provide insights and recommendations based on model performance.

3. Repository Structure
Staywise-Airbnb-Pricing/
│
├── notebooks/
│   ├── 01_data_loading_eda.ipynb
│   ├── 02_preprocessing_feature_engineering.ipynb
│   ├── 03_modeling_mlflow_explainability.ipynb
│
├── src/
│   ├── data.py
│   ├── process.py
│   ├── train.py
│   └── utils.py
│
├── docs/
│   └── screenshots/
│       ├── mlflow_runs.png
│       ├── mlflow_metrics.png
│       ├── mlflow_artifacts.png
│       └── mlflow_registry.png
│
├── artifacts/
│   ├── airbnb_preprocessor.joblib
│   ├── shap_summary.png
│   ├── shap_dependence.png
│
├── data/
│   ├── sample_processed.parquet
│
├── requirements.txt
├── .gitignore
└── README.md

4. Setup Instructions
4.1. Clone the repository
git clone https://github.com/Gr8man07/Staywise-Airbnb-Pricing.git
cd Staywise-Airbnb-Pricing

4.2. Create and activate a virtual environment
python -m venv venv
venv\Scripts\activate

4.3. Install the dependencies
pip install -r requirements.txt

4.4. Configure AWS credentials

Create a .env file in the project root:

AWS_ACCESS_KEY_ID=YOUR_KEY
AWS_SECRET_ACCESS_KEY=YOUR_SECRET
AWS_REGION=us-east-2
S3_PATH=s3://my-airbnb-pricing/AB_NYC_2019.csv

5. Running the Workflow
5.1. Launch MLflow UI
mlflow ui


Your dashboard will look similar to the screenshots below:

<img width="494" height="380" alt="MLflow Screenshot 1" src="https://github.com/user-attachments/assets/68378d7e-9be0-49d0-b051-908049f2e46a" /> <img width="921" height="452" alt="MLflow Screenshot 2" src="https://github.com/user-attachments/assets/6aebdc07-faf9-4a0c-81ac-3e0dd8b9a133" /> <img width="912" height="457" alt="MLflow Screenshot 3" src="https://github.com/user-attachments/assets/ccfe600b-0673-4d6e-b615-882f7c715a5c" />

Access MLflow here:
http://127.0.0.1:5000

5.2. Run the training pipeline
python src/train.py

6. MLflow Graphics
6.1. Experiment Runs Overview
<img width="296" height="184" src="https://github.com/user-attachments/assets/93e1c561-4d2b-415b-8030-73c6c2f7bd70" />
6.2. Metrics Comparison
<img width="185" height="65" src="https://github.com/user-attachments/assets/c2a5dd88-80a9-4e79-8348-949f40d4522f" />
6.3. Logged Artifacts
<img width="230" height="142" src="https://github.com/user-attachments/assets/553611b9-1818-4be2-9d7e-b2fa24531986" /> <img width="481" height="306" src="https://github.com/user-attachments/assets/8ab59fa7-63d5-4b94-b750-b99d9a77b910" /> <img width="480" height="314" src="https://github.com/user-attachments/assets/6a625b65-b31e-4563-a008-cb081ab0e8fa" />
7. Key Findings & Insights
7.1. Data Insights

Prices vary significantly by neighbourhood—Manhattan being the highest.

Listings with more reviews tend to have more stable pricing patterns.

Several numeric fields required imputation due to missing values.

7.2. Feature Engineering Observations

Log-transforming price greatly stabilized variance.

Reviews per month and host listing count improved model separation.

Latitude and longitude offer strong predictive power for location.

7.3. Model Performance

The Random Forest Regressor achieved the best RMSE after preprocessing.

One-hot encoding + scaling yielded significant improvements.

7.4. Explainability (SHAP)

Neighbourhood and room_type are the strongest predictors.

Availability_365 and host listing count influence pricing.

SHAP visualizations clearly show feature impact.

<img width="298" height="358" src="https://github.com/user-attachments/assets/e59c627f-a5ad-4a29-871e-0b7a85303959" /> <img width="266" height="178" src="https://github.com/user-attachments/assets/a4ec5596-70f8-4c17-a5f6-de9ccb43821f" /> <img width="269" height="203" src="https://github.com/user-attachments/assets/b48bbe1c-43c7-4240-8691-b4fdbbcc717c" />

8. Recommendations for StayWise

Integrate the model into the host onboarding workflow to provide live price suggestions.

Schedule monthly retraining using MLflow to keep the model fresh.

Expand with additional time-dependent (seasonal) and spatial features.

Evaluate more advanced models such as XGBoost or LightGBM.

9. Conclusion

This project successfully delivers a robust, end-to-end ML workflow for predicting Airbnb listing prices using AWS S3 and MLflow.
With clean preprocessing, strong feature engineering, and thorough experiment tracking, the solution provides meaningful predictive accuracy and business value for StayWise.
