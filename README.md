# 🛡️ Insurance Charges Predictor

**An end-to-end machine learning application for insurance cost analysis and prediction.**

**Author:** Rohit Singh  
**Program:** B.Tech — Electrical & Electronics Engineering  
**Institute:** NITK Surathkal

## 🚀 Live Demo

👉 **[Open the Insurance Charges Predictor](PASTE_YOUR_STREAMLIT_LINK_HERE)**

The deployed Streamlit application lets users explore the dataset, perform interactive EDA, enter applicant information, generate insurance-charge predictions, and review model performance.

> Replace `PASTE_YOUR_STREAMLIT_LINK_HERE` with your actual Streamlit app URL.

## 📌 Project Overview

The goal is to predict an individual's **medical insurance charges** using demographic, lifestyle, coverage, and medical-history information.

**Workflow:** Raw Data → Data Cleaning → EDA → Feature Engineering → Data Transformation → Model Training & Tuning → Model Evaluation → Streamlit Application

### Dataset Features
- **Numerical:** `age`, `bmi`, `children`
- **Categorical:** `gender`, `smoker`, `region`, `medical_history`, `family_medical_history`, `exercise_frequency`, `occupation`, `coverage_level`
- **Target:** `charges`

## 🏗️ Project Architecture

```text
Raw CSV Dataset
       │
       ▼
Data Ingestion & Cleaning
       │
       ▼
Feature Engineering
       ├── BMI category
       ├── Age group
       ├── Smoker × BMI interaction
       └── Missingness indicators
       │
       ▼
Data Transformation
       ├── Median imputation
       ├── Standard scaling
       ├── One-hot encoding
       └── Ordinal encoding
       │
       ▼
Model Training & Tuning
       ├── Linear Regression
       ├── Ridge
       ├── ElasticNet
       ├── Random Forest
       └── XGBoost
       │
       ▼
Model Evaluation
       ├── R²
       ├── Adjusted R²
       ├── MAE
       ├── RMSE
       ├── MAPE
       └── Diagnostic plots
       │
       ▼
Streamlit Application
```

## 📊 Exploratory Data Analysis

The application provides interactive EDA to understand the data and relationships associated with insurance charges.

### Univariate Analysis
- Numerical distributions
- Categorical distributions
- Insurance-charge distribution
- Quartiles and skewness

### Bivariate / Multivariate Analysis
- Numerical features vs. insurance charges
- Trend analysis
- Two-way categorical comparisons
- Smoker × BMI interaction
- Smoker × Age interaction
- Pairwise numerical relationships

### Data Quality
- Missing-value counts
- Missingness patterns
- Duplicate-row checks
- Schema checks

### Outlier Detection
- IQR-based outlier detection
- Box-plot inspection
- Charge outliers by smoking status

### Feature Engineering Validation
- `bmi_category`
- `age_group`
- `smoker_bmi_interaction`
- `medical_history_missing`
- `family_medical_history_missing`

## 🧩 Feature Engineering

### BMI Category
```text
Underweight → Normal → Overweight → Obese
```

### Age Group
```text
18-25 → 26-35 → 36-45 → 46-55 → 56-65
```

### Smoker × BMI Interaction
```text
smoker_bmi_interaction = BMI × is_smoker
```

### Missingness Indicators
Missing values in `medical_history` and `family_medical_history` are represented using missingness indicators, while categorical missing values are handled as `"Unknown"` during preprocessing.

## 🤖 Machine Learning

The training pipeline compares multiple regression models:

| Model | Purpose |
|---|---|
| Linear Regression | Interpretable baseline |
| Ridge | Regularized linear model |
| ElasticNet | L1 + L2 regularization |
| Random Forest | Non-linear ensemble model |
| XGBoost | Gradient-boosted tree model |

Tunable models use:
- `RandomizedSearchCV`
- 5-fold cross-validation
- R² scoring
- Configurable search iterations

The final model is selected using validation performance and cross-validation stability, while considering model simplicity and interpretability.

## 📈 Model Evaluation

The final selected model is evaluated on a held-out test set using:

- **R²**
- **Adjusted R²**
- **MAE**
- **RMSE**
- **MAPE**

### Diagnostic Plots
- Actual vs. Predicted
- Residual Analysis
- Q-Q Plot
- Feature Importance
- Learning Curve

## 🖥️ Streamlit Application

### 📊 Dataset Overview
Shows row/column counts, missing values, duplicate rows, dataset preview, and feature schema.

### 🔎 Exploratory Analysis
Interactive visual analysis covering univariate analysis, bivariate/multivariate relationships, missing data, outliers, and feature-engineering validation.

### 💰 Predict
Users enter applicant information including age, gender, BMI, children, smoking status, region, occupation, coverage level, exercise frequency, medical history, and family medical history. The application then generates a predicted insurance charge using the persisted preprocessing pipeline and trained model.

### 📈 Model Performance
Shows the champion model, test metrics, model comparison, validation R² comparison, and diagnostic plots.

### ℹ️ About
Provides an overview of the project, modelling workflow, and technology stack.

## 📁 Project Structure

```text
Insurance-Charges-Predictor/
│
├── config.yaml
├── main.py
├── requirements.txt
├── setup.py
├── README.md
│
├── data/
│   ├── raw/
│   └── processed/
│
├── artifacts/
│   ├── preprocessor.pkl
│   ├── best_model.pkl
│   ├── model_metadata.json
│   ├── model_comparison.csv
│   ├── evaluation_report.json
│   └── plots/
│
├── src/
│   ├── components/
│   │   ├── data_ingestion.py
│   │   ├── data_transformation.py
│   │   ├── model_trainer.py
│   │   └── model_evaluation.py
│   ├── pipeline/
│   │   ├── train_pipeline.py
│   │   └── predict_pipeline.py
│   ├── utils.py
│   ├── logger.py
│   └── exception.py
│
└── streamlit_app/
    └── app.py
```

## ⚙️ Configuration

`config.yaml` acts as the central configuration file for dataset paths, train/validation/test split, feature schema, cross-validation settings, XGBoost settings, model flags, hyperparameter search spaces, and artifact paths.

## 🚀 Installation

```bash
git clone https://github.com/rohit3481/Insurance-Charges-Predictor.git
cd Insurance-Charges-Predictor
python -m venv .venv
```

Windows:
```bash
.venv\Scripts\activate
```

Linux/macOS:
```bash
source .venv/bin/activate
```

Install dependencies:
```bash
pip install -r requirements.txt
```

## ▶️ Run the Training Pipeline

```bash
python main.py
```

This executes:

```text
Data Ingestion
      ↓
Feature Engineering
      ↓
Data Transformation
      ↓
Model Training & Tuning
      ↓
Model Selection
      ↓
Model Evaluation
```

## 🌐 Run the Streamlit Application Locally

```bash
streamlit run streamlit_app/app.py
```

For the easiest experience, use the **Live Demo** link at the top of this README.

## 🛠️ Technology Stack

| Area | Technology |
|---|---|
| Language | Python |
| Data Analysis | Pandas, NumPy |
| Visualization | Plotly |
| Machine Learning | Scikit-learn |
| Gradient Boosting | XGBoost |
| Frontend | Streamlit |
| Configuration | YAML |
| Model Persistence | Joblib |

## 🎯 What This Project Demonstrates

- Exploratory Data Analysis
- Data Cleaning
- Feature Engineering
- Regression Modelling
- Hyperparameter Tuning
- Cross-Validation
- Model Selection
- Model Evaluation
- Data Visualization
- Streamlit Application Development
- Configuration-driven ML workflow
- End-to-end data-to-application development

## 👤 Author

**Rohit Singh**  
B.Tech — Electrical & Electronics Engineering  
**NITK Surathkal**

[GitHub](https://github.com/rohit3481)
