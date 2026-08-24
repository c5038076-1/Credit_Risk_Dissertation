# Credit_Risk_Dissertation

# Author Name : Kalyan Babu Kalapala 

# Student id : 35038076 
## Project Overview

This dissertation develops and evaluates a Machine Learning based credit-risk prediction workflow for bank customers and integrates the selected model into a Prototype Decision Support System.

The project evaluates four Machine Learning models: Random Forest, XGBoost, LightGBM, and CatBoost. The workflow includes data preprocessing, missing-value treatment, duplicate removal, categorical encoding, train-test splitting, class balancing with SMOTE, baseline model evaluation, hyperparameter optimisation using RandomizedSearchCV with cross-validation, SHAP analysis, prototype development, and human evaluation.

The final selected model is the optimised CatBoost model because it achieved the strongest overall F1-Score and high performance across the other evaluation measures.

## Project Title

Evaluating Machine Learning Models for Bank Customer Credit Risk Prediction with a Prototype Decision Support System

## Aim

The aim is to evaluate Machine Learning models for bank customer credit-risk prediction, optimise their predictive performance, develop a prototype decision support system, and assess the prototype through human evaluation.

## Research Question

How can Machine Learning models be evaluated for bank customer credit risk prediction, optimised for improved predictive performance, and integrated into a prototype decision support system that is assessed through human evaluation and participant feedback?

## Dataset

The Credit Risk dataset was obtained from Kaggle. The original dataset contains 32,581 records and 12 variables covering customer demographic, financial, employment, loan, and credit-history information.

The target variable is `loan_status`, representing the loan-risk outcome.

During data quality processing, missing values were identified in `person_emp_length` and `loan_int_rate`. Duplicate records were also checked and removed. The resulting cleaned dataset contained 32,416 observations.

The dataset contains both numerical and categorical variables. Categorical variables such as home ownership, loan intent, loan grade, and previous default were encoded before model training.

## Data Preprocessing

The preprocessing workflow consisted of the following stages:

1. Dataset loading and inspection
2. Missing-value identification and treatment
3. Duplicate record checking and removal
4. Categorical feature encoding
5. Target variable preparation
6. 80:20 train-test split
7. Class-distribution assessment
8. SMOTE applied to the training data
9. Model training and evaluation

The dataset was divided into 25,932 training records and 6,484 testing records.

SMOTE was applied only to the training data to address class imbalance and improve the ability of the models to learn patterns from the minority class.

## Machine Learning Models

Four ensemble Machine Learning models were implemented.

### Random Forest

Random Forest was used as a benchmark ensemble model. It provides a reliable baseline for structured classification and can model nonlinear relationships using multiple decision trees.

### XGBoost

XGBoost was selected because of its strong predictive performance for structured datasets and its gradient boosting framework.

### LightGBM

LightGBM was included because it provides efficient gradient boosting and is suitable for structured financial datasets.

### CatBoost

CatBoost was selected because of its strong performance on structured data and its gradient boosting approach. It achieved the strongest overall performance in this project and was selected as the final model.

## Evaluation Metrics

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC

F1-Score was particularly important because it balances Precision and Recall. This is relevant to credit-risk prediction because both reliable positive predictions and identification of high-risk customers are important.

## Baseline Results

The baseline model results were:

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| XGBoost | 93.20% | 92.10% | 75.30% | 82.89% | 93.21% |
| LightGBM | 92.81% | 91.40% | 74.10% | 81.85% | 93.55% |
| Random Forest | 90.39% | 79.51% | 75.53% | 77.47% | 91.88% |
| CatBoost | 93.54% | 95.20% | 74.19% | 83.39% | 93.88% |

CatBoost achieved the highest baseline Accuracy, Precision, F1-Score, and ROC-AUC among the four models.

The baseline results showed that the boosting models generally performed better than Random Forest for this structured credit-risk dataset.

## Hyperparameter Optimisation

Hyperparameter optimisation was performed using RandomizedSearchCV with cross-validation.

Randomized Search was selected because it can explore a broad parameter space without testing every possible parameter combination. This provides an efficient approach for tuning ensemble models with multiple hyperparameters.

After optimisation, each model was retrained using its selected configuration and evaluated on the independent testing dataset using the same metrics as the baseline experiments.

## Optimised Results

The final optimised results were:

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| XGBoost | 92.83% | 91.04% | 74.54% | 81.97% | 93.46% |
| LightGBM | 93.20% | 92.96% | 74.54% | 82.74% | 94.32% |
| Random Forest | 90.02% | 78.20% | 75.39% | 76.77% | 91.77% |
| CatBoost | 93.45% | 95.26% | 73.70% | 83.10% | 93.48% |

## Best Performing Model

The optimised CatBoost model was selected as the final model.

Its final performance was:

- Accuracy: 93.45%
- Precision: 95.26%
- Recall: 73.70%
- F1-Score: 83.10%
- ROC-AUC: 93.48%

CatBoost achieved the highest F1-Score of the evaluated optimised models.

The F1-Score results were:

| Model | Optimised F1-Score |
|---|---:|
| CatBoost | 83.10% |
| LightGBM | 82.74% |
| XGBoost | 81.97% |
| Random Forest | 76.77% |

The final model was therefore integrated into the prototype.

## SHAP Analysis

SHAP analysis was applied to the optimised CatBoost model to identify the features that contributed most strongly to the predictions.

The main features identified were:

1. `loan_percent_income`
2. `person_emp_length`
3. `person_income`
4. `loan_int_rate`
5. `person_home_ownership`
6. `loan_intent`
7. `loan_grade`
8. `person_age`
9. `cb_person_cred_hist_length`
10. `loan_amnt`
11. `cb_person_default_on_file`

The most influential feature was `loan_percent_income`.

The SHAP results indicate that loan affordability, employment characteristics, income, and borrowing conditions were important factors in the CatBoost predictions.

## Prototype

The optimised CatBoost model was integrated into an interactive Customer Credit Risk Prediction Prototype.

The prototype allows users to enter:

- Age
- Annual income
- Home ownership
- Employment length
- Loan intent
- Loan grade
- Loan amount
- Interest rate
- Loan percentage of income
- Previous default
- Credit history length

The prototype processes the entered information and produces a credit-risk classification.

The interface includes input fields, prediction output, reset functionality, and an exit option.

## Prototype Scenario Results

Two example scenarios were evaluated.

### Scenario 1: High Credit Risk

A customer with an annual income of 24,000, short employment and credit history, an E-grade loan, an interest rate of 18.5%, and a loan amount of 18,000 received a HIGH CREDIT RISK prediction.

### Scenario 2: Low Credit Risk

A 30-year-old customer with an annual income of 85,000, 9 years of employment experience, 10 years of credit history, an A-grade loan, and a 7.5% interest rate received a LOW CREDIT RISK prediction.

These scenarios demonstrate that the prototype can process customer information and produce different credit-risk classifications based on the supplied customer and loan characteristics.

## Human Evaluation

Human evaluation was conducted to assess the prototype from the user perspective.

The questionnaire assessed:

- Ease of use
- Prediction clarity
- Interface quality
- Prediction speed
- Overall usefulness
- Overall satisfaction

A five-point rating scale was used, where 5 represented the most positive perception.

A total of 200 response items were evaluated. The overall average rating was 4.50 out of 5.00.

The results indicate a very positive user response. Participants generally considered the prototype easy to use, understandable, suitable, and helpful for credit-risk assessment.

## Strengths

The main strengths of the project are:

- End-to-end Machine Learning workflow
- Structured preprocessing and data cleaning
- Class balancing using SMOTE
- Evaluation of four ensemble models
- Baseline and optimised model evaluation
- RandomizedSearchCV based hyperparameter optimisation
- F1-Score based final model selection
- SHAP feature analysis
- Interactive prototype development
- Human evaluation of prototype usability
- Integration of technical and user-centred evaluation

## Limitations

The project has several limitations.

The evaluation was performed using a single publicly available dataset. Therefore, the results may not represent all banking populations and lending environments.

The optimised CatBoost model achieved a Recall of 73.70%, which indicates that some high-risk customers were not identified.

The prototype was evaluated within the dissertation setting rather than in a real financial institution. Therefore, the results do not establish operational deployment in a live banking environment.

Dedicated fairness metrics were outside the scope of the implementation, although fairness remains an important consideration for credit-risk prediction.

## Future Work

Future work should validate the selected model using additional banking datasets and different lending environments.

Future studies should also introduce dedicated fairness measures to investigate whether predictions differ across customer groups.

Further SHAP-based analysis could be used for subgroup and fairness assessment.

Future research could also investigate more advanced or hybrid Machine Learning approaches while maintaining practical usability and feature-level analysis.


## Technology Stack

The project uses Python and Jupyter Notebook for development.

The main tools and libraries include:

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- LightGBM
- Random Forest
- CatBoost
- RandomizedSearchCV
- Matplotlib
- Seaborn
- SHAP
- Tkinter
- CSV
- Joblib

## General Workflow

```text
Credit Risk Dataset
        |
        v
Data Cleaning
        |
        v
Missing Value Treatment
        |
        v
Duplicate Removal
        |
        v
Categorical Encoding
        |
        v
Train-Test Split
        |
        v
SMOTE on Training Data
        |
        v
Baseline Models
        |
        v
Performance Evaluation
        |
        v
RandomizedSearchCV
        |
        v
Optimised Models
        |
        v
F1-Score Based Model Selection
        |
        v
Optimised CatBoost
        |
        v
SHAP Analysis
        |
        v
Prototype Development
        |
        v
Human Evaluation
```

## Ethics and Data Governance

The dissertation uses a secondary Credit Risk dataset and addresses ethical considerations including privacy, data protection, consent, responsible human evaluation, secure data handling, prediction bias, and data retention.

Human evaluation was conducted voluntarily and anonymously. Appropriate data governance and deletion procedures were considered as part of the project.

## Reproducibility

To reproduce the modelling workflow, the dataset should be placed in the appropriate data directory and the preprocessing, model training, optimisation, SHAP analysis, and prototype stages should be executed in sequence.

The same preprocessing and evaluation procedures should be maintained when reproducing the reported results.

The reported final model is the optimised CatBoost model with an F1-Score of 83.10%.

## Key Findings

The main findings of the dissertation are:

1. The four selected ensemble Machine Learning models were capable of predicting bank customer credit risk from structured customer and loan information.
2. CatBoost achieved the strongest baseline performance with an F1-Score of 83.39%.
3. After hyperparameter optimisation, CatBoost remained the strongest model with an F1-Score of 83.10%.
4. CatBoost achieved 93.45% Accuracy, 95.26% Precision, 73.70% Recall, and 93.48% ROC-AUC after optimisation.
5. `loan_percent_income` was the most influential feature identified by SHAP.
6. The optimised CatBoost model was successfully integrated into an interactive prototype.
7. The prototype produced different credit-risk outcomes for different customer scenarios.
8. Human evaluation produced an overall average rating of 4.50 out of 5.00 across 200 response items.
9. The main limitation is the use of a single public dataset and the relatively lower Recall for identifying some high-risk customers.

## Conclusion

The project demonstrates an end-to-end Machine Learning workflow for bank customer credit-risk prediction. The workflow combines preprocessing, class balancing, model evaluation, hyperparameter optimisation, SHAP analysis, prototype development, and human evaluation.

The optimised CatBoost model provided the strongest overall F1-Score and was selected for integration into the prototype decision support system. The human evaluation results also provided positive evidence regarding the practical usability and usefulness of the prototype.



Evaluating Machine Learning Models for Bank Customer Credit Risk Prediction with a Prototype Decision Support System
