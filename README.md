# Machine Learning-Based Crop Yield Forecasting for European Agriculture

This dissertation was carried out by Konstantinos Katsantouris and supervised by Dr Ioanna Stamatopoulou as part of the MSc in Artificial Intelligence and Data Science (2025–2026).

---

## Repository Structure

The repository follows a modular structure, where each folder and notebook corresponds to a stage of the research pipeline:

- **`data/`**
  - `draft/`: Sets for testing purposes during implementation (just for reference)
  - `final/`: Preprocessed train/test sets
  - `processed/`: Cleaned and merged datasets  
  - `raw/`: Original datasets from FAOSTAT and World Bank CCKP  

- **`models/`**: Trained models

- **`notebooks/`**
  - `01_merge_raw_data.ipynb`: Data integration and cleaning  
  - `02_exploratory_data_analysis.ipynb`: Exploratory analysis, plots, and correlations  
  - `03_dataset_preprocessing.ipynb`: Preprocessing and dataset preparation  
  - `04_modeling.ipynb`: Model training, tuning, and evaluation  
  - `05_xai.ipynb`: Explainable AI analysis (SHAP, LIME, feature importance)  

- **`results/`**
  - `eda/`: Exploratory plots and visualizations  
  - `gradient_boosting/`: Evaluation metrics for GB
  - `linear_regression/`: Evaluation metrics for LR
  - `mlp/`: Evaluation metrics for MLP
  - `random_forrest/`: Evaluation metrics for RF
  - `svr/`: Evaluation metrics for SVR
  - `xai/`: Explainable AI outputs (SHAP, LIME explanations)
  - `xgboost/`: Evaluation metrics for XGB

---

## Workflow

The research workflow is organized into **five main notebooks**:

### 1. `01_merge_raw_data.ipynb`
This stage brings together the raw inputs:
- Harmonizes country names  
- Merges FAOSTAT datasets (yield, area, production)  
- Drops obsolete countries and year 2023  
- Merges with World Bank CCKP climate indicators  
- **Output:** cleaned dataset in `data/processed`

### 2. `02_exploratory_data_analysis.ipynb`
Exploratory data analysis of the merged dataset:
- Maps countries to four European regions  
- Filters the time window (2012–2020)  
- Analyzes yield trends and highlights extreme years  
- Computes statistics on production and harvested area  
- Groups indicators into heatwave, drought, and frost categories  
- Performs correlation analysis between climate indicators and yield  
- **Output:** plots in `results/eda`

### 3. `03_dataset_preprocessing.ipynb`
Preparation of the final dataset for modeling:
- Drops non-correlated columns  
- Ensures correct numeric types  
- Detects outliers and removes duplicates  
- One-hot encodes crop categories  
- Scales numeric features  
- Splits data into 80/20 balanced train/test sets  
- **Output:** preprocessed data in `data/final`

### 4. `04_modeling.ipynb`
Model training and evaluation:
- Performs extensive Grid Search with cross-validation  
- Selects the best hyperparameters for each model  
- Evaluates performance using RMSE, MAE, MSE, R², and MAPE  
- Saves trained models and metrics for later use  
- **Output:** models in `models` and metrics in folders with the model's name under `results`

### 5. `05_xai.ipynb`
Explainability of the best-performing model:
- Computes feature importance  
- Applies SHAP for global and local explanations  
- Applies LIME for local explanations  
- Saves results for interpretability analysis  
- **Output:** results in `results/xai`

---
