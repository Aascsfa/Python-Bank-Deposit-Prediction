# Bank Deposit Prediction
Note: This is the first three section of the notebook

## Problem and Context
This project focuses on evaluating the effectiveness of a direct marketing campaign for a Portuguese bank using machine learning. The goal is to predict whether a customer subscribed to a term deposit after the campaign. The dataset, available on Kaggle, includes over 45,000 rows and 17 attributes.
Link: https://www.kaggle.com/datasets/yufengsui/portuguese-bank-marketing-data-set

## Importance of Customer Term Deposits and Project Necessity
In the aftermath of the 2008 Global Financial Crisis, customer confidence in banks was low, impacting the bank's liquidity. Sufficient customer term deposits are crucial for the bank to maintain operations, comply with regulations, and lend money. The bank seeks to identify factors influencing customers' decisions to subscribe to term deposits. Manual analysis of such a large dataset would be resource-intensive and time-consuming. Machine learning offers an efficient alternative by identifying patterns and predicting customer behaviour based on their attributes. The model developed can also be adapted for similar future scenarios.

## Step by Step Solution
**Session 1: Extract, Transform and Load dataset**
- Extract data, overview data, preprocessing, EDA, and label encode.

**Session 2: Training, testing and validating data**
- Form the training, testing and validating dataset then resample the data.

**Session 3: Classifier construction**
- Develop classifiers by training machine learning models, solve the target classification problem then evaluate the model using various metrics.

**Session 4: Improve best model (XGBoost)**
- Overview about the the best model first, then create the stacking model, perform hyperparameter tuning, Feature Importance and Feature Removal to improve the model

**Session 5: Final decision**
- Decide the best models to deploy based on different business goals.

## Important processes, findings and results
In **Session 1**, hidden null values was discovered as "unknown" in categorical columns, even though there is no null values across the 17 attributes. The poutcome column was removed due to 82% of its values being "unknown." The target variable was highly imbalanced, with 5,000 "yes" and 40,000 "no" label.  To manage outliers but without removing them, numerical columns were binned based on demographic relevance and their impact on the target variable. Following Exploratory Data Analysis (EDA), key findings were summarized at the start of session 1.3. We then transformed the dataset through one-hot encoding, retaining only month and y as label-encoded variables. After splitting the data in **Session 2**,  SMOTE was applied again to balance the target variable, resulting in 28,000 instances each of "yes" and "no."

**Session 3** involved training and evaluating machine learning models. A total of eight models were tested, with tree-based models like XGBoost and Gradient Boosting outperforming the rest. For non-technical stakeholders, a brief overview on the usage of evaluation metrics was provided at the end.


After initial modeling, **Session 4** focused on improving the XGBoost's performance. First, I have tried to combine different models to leverage their strengths in sesion 4.2. While the models performed well on the resampled testing set, results were less favorable when applied to the original imbalanced test data, particularly for class 1 predictions.

- In session 4.3, hyperparameter tuning was performed on XGBoost with a focus on improving recall for class 1. The result significantly improve, with model 1 capturing 98% of class 1 but with only 23% precision. Subsequent tuning for F1 and precision (Models 3 to 6) did not significantly improve class 1 performance, with F1, precision, and recall ranging between 45%-60%.

- In session 4.4, less important features were removed (<1% importance), and the default parameter did not improve the performance (Model 7 and 8) so hyperparameter tuning was continued, with Models 10 and 11 showing more balanced improvements (precision of 51% and recall of 73%).

- Recognizing the challenge of training on balanced data and testing on imbalanced data, **Session 4.5 involved training without SMOTE**. The eight model was trained and evaluated again, with XGBoost and Naive Bayes emerged as top performers.
  - XGBoost excelling in precision for class 1 and Naive Bayes achieving better recall for class 1. Both models performed well for class 0.
  - In Session 4.5.2, I combined XGBoost and Naive Bayes to optimize both recall and F1. Models 12 to 19 showed incremental improvements, with recall stabilizing at 78% and precision around 52%. Among the final models, the best performance achieved 90% recall and 42% precision, but further model combinations (Sessions 4.5.3 and 4.5.4) yielded no significant improvements.


In **session 5**, I have selected three models based on different objectives, offering a clear comparison of their strengths and trade-offs.:
1. xgb_recall_model1 (highest recall, lowest precision): capture a larger portion of potential subscribers, but result in targeting some customers less likely to subscribe.
2. best_model_23 (balanced recall and precision): strikes a balance between recall and precision, making it a strong choice when it’s important to both capture a good number of subscribers and avoid over-targeting.
3. best_model_16 (highest precision, lowest recall): effectively identifying subscribers most likely to engage, but at the cost of missing some potential subscribers.









