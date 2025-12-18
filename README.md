# Vaccine Uptake Prediction Project

[Flu Vaccine](Images/flu-vaccine.jpg)

## Overview

This project develops machine learning models to predict whether individuals received the H1N1 vaccine based on demographic information, health behaviors, and personal opinions collected from the National 2009 H1N1 Flu Survey. By identifying key factors that influence vaccination decisions, this analysis provides actionable insights for public health officials to design more effective vaccination campaigns and address vaccine hesitancy.

## Business and Data Understanding
Stakeholder Audience

The primary stakeholders are public health officials and policymakers who aim to improve vaccination campaigns and resource allocation. Understanding which factors influence vaccine uptake enables targeted public health interventions and more effective communication strategies.

## Dataset Understanding

The dataset contains survey responses from the National 2009 H1N1 Flu Survey with:

26,707 training observations and 26,708 test observations
33 features after preprocessing, including:

Demographics: age group, education, race, sex, income, marital status, employment
Health behaviors: mask usage, hand washing, social distancing practices
Health status: chronic medical conditions, health insurance, healthcare worker status
Opinions: perceived risk of H1N1, belief in vaccine effectiveness, concerns about side effects
Contextual factors: geographic region, household composition

Target Variable: Binary indicator of whether the individual received the H1N1 vaccine (0 = No, 1 = Yes)

Key Challenge: The dataset exhibits significant class imbalance, with approximately 78% of respondents NOT receiving the vaccine and only 22% receiving it. This imbalance requires careful model selection and evaluation using metrics beyond simple accuracy.

## Data Preparation

Missing value imputation:

Median imputation for numerical features
Mode imputation for categorical features


Feature engineering: Dropped employment-related features with >50% missing values
Train-test split: 80/20 split with stratification to maintain class balance
Preprocessing pipeline:

StandardScaler for numerical features (used in Logistic Regression)
OneHotEncoder for categorical features (drop='first' to avoid multicollinearity)
No scaling for tree-based models (Decision Trees are scale-invariant)

Critical consideration: All transformers were fit on training data only and then applied to both train and test sets to prevent data leakage.

## Modeling

An iterative approach was used, progressing from simple baseline models to tuned models. All models used class_weight='balanced' to address class imbalance, and hyperparameter tuning prioritized recall to align with the public health goal of identifying potential vaccinees.

- Baseline Logistic Regression
Simple, interpretable baseline model. Achieved 77.2% accuracy, 0.8237 ROC-AUC with high recall (0.72) for identifying vaccinated individuals, though with lower precision (0.48).

- Tuned Logistic Regression
GridSearchCV optimized regularization (C parameter) and solver. Performance remained similar to baseline (77.1% accuracy, 0.8228 ROC-AUC, 0.72 recall), validating the baseline approach.

- Baseline Decision Tree
Captures non-linear relationships without requiring feature scaling. Lower performance (75.3% accuracy, 0.636 ROC-AUC) indicated overfitting, motivating tuning.

- Tuned Decision Tree
Hyperparameters (max_depth, min_samples_split, min_samples_leaf, criterion) optimized via GridSearchCV. Best overall performance: 77.9% accuracy, 0.809 ROC-AUC, 0.68 recall, successfully balancing complexity and generalization.

## Evaluation

Best Model Selection
Baseline Logistic Regression is selected as the final model based on:

Highest ROC-AUC score (0.8237): Good ability to distinguish between those who will and won't get vaccinated.
Highest accuracy (77.2%): Most correct predictions overall.
Strong recall (0.72): Identifies 68% of vaccinated individuals.
Highest f1 score(0.5769) which is the best balance between recall and precision.
Balanced performance: Good trade-off between precision and recall.

## Conclusion

This study demonstrates that vaccine uptake is strongly influenced by individual perceptions and behaviors rather than demographics alone. While Logistic Regression offered interpretability and strong baseline performance, tuned models improved prediction confidence by reducing false positives.

Class imbalance presents an inherent trade-off. Higher recall models identify more vaccinees but generate more false positives. Higher precision models are more confident but miss more vaccinees.

## Reccomendations
- Strengthen doctor-patient communication.
- Address vaccine effectiveness misconceptions.
- Reduce percieved barriers and risks.
- Target individuals with high concern but low vaccination rates.

