# Staywise-Airbnb-Pricing
Airbnb nightly price prediction with MLflow + S3
# StayWise Airbnb Pricing Prediction  
Predicting Nightly Listing Prices Using AWS S3, MLflow, and Machine Learning

## 1. Project Overview
StayWise is a global vacation rental platform that aims to provide hosts with accurate, data-driven pricing recommendations. Nightly listing prices vary widely across New York City, influenced by factors such as neighbourhood, property type, host activity, and guest reviews.  

This project delivers a complete machine learning solution that predicts nightly listing prices using the Airbnb NYC 2019 dataset stored in AWS S3.  
The solution follows a modern, reproducible workflow supported by **MLflow** for experiment tracking and model management.

The final deliverable includes data loading, preprocessing, feature engineering, model training, experiment comparison, explainability analysis, and model registration.

---

## 2. Objectives
This project was designed with the following objectives:

- Retrieve the Airbnb listing dataset directly from **AWS S3** using secure programmatic access.
- Perform comprehensive **data cleaning** to address missing values, inconsistencies, and outliers.
- Apply meaningful **feature engineering** to enrich model inputs.
- Build and compare multiple **regression models** for accurate price prediction.
- Track all experiments using **MLflow**, capturing parameters, metrics, and artifacts.
- Register the best-performing model for production use.
- Present results, insights, and recommendations in a reusable research workflow.

---

## 3. Repository Structure

Staywise-Airbnb-Pricing/
│
├── notebooks/
│ ├── 01_data_loading_eda.ipynb
│ ├── 02_preprocessing_feature_engineering.ipynb
│ ├── 03_Modeling_MlFlow_and_Explainability.ipynb
│
│
├── src/
│ ├── data.py
│ ├── process.py
│ ├── train.py
│ └── utils.py
│
├── docs/
│ └── screenshots/
│ ├── mlflow_runs.png
│ ├── mlflow_metrics.png
│ ├── mlflow_artifacts.png
│ └── mlflow_registry.png
│
├── artifacts/
│ ├── airbnb_preprocessor.joblib
│ ├── shap_summary.png
│ ├── shap_dependence.png
│
├── data/
│ ├── sample_processed.parquet
│
├── requirements.txt
├── .gitignore
├── README.md
└── LICENSE (optional)


---

## 4. Setup Instructions

### **4.1. Clone the repository**
```bash
git clone https://github.com/Gr8man07/Staywise-Airbnb-Pricing.git
cd Staywise-Airbnb-Pricing

### **4.2. Create and activate a virtual environment
python -m venv venv
venv\Scripts\activate

### **4.3. Install project dependencies
pip install -r requirements.txt

### **4.4. Configure AWS credentials

Create a .env file in the project root:

AWS_ACCESS_KEY_ID=YOUR_KEY  
AWS_SECRET_ACCESS_KEY=YOUR_SECRET  
AWS_REGION=us-east-2
S3_PATH=s3://my-airbnb-pricing/AB_NYC_2019.csv

## 5. Running the Workflow

### **5.1. Launch MLflow UI
mlflow ui
<img width="494" height="380" alt="image" src="https://github.com/user-attachments/assets/68378d7e-9be0-49d0-b051-908049f2e46a" />

<img width="921" height="452" alt="image" src="https://github.com/user-attachments/assets/6aebdc07-faf9-4a0c-81ac-3e0dd8b9a133" />
<img width="912" height="457" alt="image" src="https://github.com/user-attachments/assets/ccfe600b-0673-4d6e-b615-882f7c715a5c" />


Open the dashboard:

http://127.0.0.1:5000

### **5.2 Run training pipeline
python src/train.py

## 6. MLflow Graphics

### **6.1. MLflow
<img width="296" height="184" alt="image" src="https://github.com/user-attachments/assets/93e1c561-4d2b-415b-8030-73c6c2f7bd70" />

### **6.2. MLflow — Metrics Comparison

<img width="185" height="65" alt="image" src="https://github.com/user-attachments/assets/c2a5dd88-80a9-4e79-8348-949f40d4522f" />

### **6.3 MLflow — Artifacts
<img width="230" height="142" alt="image" src="https://github.com/user-attachments/assets/553611b9-1818-4be2-9d7e-b2fa24531986" />
<img width="481" height="306" alt="image" src="https://github.com/user-attachments/assets/8ab59fa7-63d5-4b94-b750-b99d9a77b910" />
<img width="480" height="314" alt="image" src="https://github.com/user-attachments/assets/6a625b65-b31e-4563-a008-cb081ab0e8fa" />

## 7. Key Insights and Findings
### ** 7.1 Data Insights

Price varies heavily by neighbourhood and room type, with Manhattan listings priced significantly higher.

Properties with more reviews generally achieve more stable pricing patterns.

Several numeric features required imputation due to missing values.

### ** 7.2 Feature Engineering Impact

Taking the logarithm of price improved model stability.

Review frequency and host listing count helped differentiate host types.

Combining latitude and longitude captures neighbourhood dynamics effectively.

### ** 7.3 Model Performance

The best model (RandomForest) achieved strong predictive performance with reduced RMSE after feature scaling and OHE encoding.

### ** 7.4 Explainability Observations (SHAP)

Neighbourhood and room type were the strongest drivers of price.

Availability and host listing count contributed to price variation.

SHAP plots provided clear, interpretable insights into each feature’s effect.
<img width="298" height="358" alt="image" src="https://github.com/user-attachments/assets/e59c627f-a5ad-4a29-871e-0b7a85303959" />
<img width="266" height="178" alt="image" src="https://github.com/user-attachments/assets/a4ec5596-70f8-4c17-a5f6-de9ccb43821f" />
<img width="269" height="203" alt="image" src="https://github.com/user-attachments/assets/b48bbe1c-43c7-4240-8691-b4fdbbcc717c" />


## 8. Recommendations for StayWise

Integrate the model into host onboarding to generate real-time pricing suggestions.

Schedule monthly automated retraining through MLflow for model freshness.

Enrich training data with additional spatial features, seasonal trends, and host response rates.

Consider future expansion into time-series dynamic pricing models.

## 9. Conclusion

This project delivers a robust, reproducible workflow for predicting Airbnb listing prices using AWS S3, MLflow, and modern machine learning techniques.
By applying strong preprocessing, thoughtful feature engineering, and meticulous model tracking, the solution provides clear predictive capability and business value for StayWise.


