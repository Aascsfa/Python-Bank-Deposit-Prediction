# Bank Deposit Prediction Project

## Introduction to the project, problem and context
- This project uses machine learning to predict whether a customer will subscribe to a term deposit after a direct marketing campaign. The dataset, sourced from Kaggle, contains over 45,000 rows and 17 attributes: [Portuguese Bank Marketing Data Set](https://www.kaggle.com/datasets/yufengsui/portuguese-bank-marketing-data-set).
- Customer term deposits are crucial for maintaining bank liquidity, especially following the 2008 Global Financial Crisis. Predicting which customers will subscribe helps the bank optimize marketing efforts and enhance efficiency.

## Approach

### Step 1: Data Preprocessing
- Cleaned the dataset, handling hidden null values ("unknown") and removed irrelevant columns.

### Step 2: Forming Training, Testing, and Validation Sets
- Split the dataset into **training**, **testing**, and **validation** sets to ensure accurate model performance evaluation.
- Applied **SMOTE** to balance the training set.

### Step 3: Model Training and Evaluation
- Trained and evaluated 8 machine learning models.
- Evaluated using key metrics: **precision**, **recall**, and **F1-score**.

### Step 4: Model Improvement
- Performed hyperparameter tuning, feature selection, combined-model, ... to enhance model performance.

### Step 5: Final Model Selection
- Select three models to deploy based on their strengths, weaknesses, and the goal of future campaigns.
