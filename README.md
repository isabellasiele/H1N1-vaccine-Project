# Vaccine Uptake Prediction Project
## Objective

To develop a classification model that predicts whether individuals received the H1N1 vaccine using demographic characteristics, health-related behaviors, and personal opinions reported in survey data.

## Overview

This project focuses on predicting H1N1 vaccine uptake using survey data that captures individuals’ backgrounds, behaviors, and perceptions related to health and vaccination. Multiple machine learning models were built and evaluated to identify the most effective approach for predicting vaccine uptake while addressing class imbalance and performance trade-offs.

Business and Data Understanding
Stakeholder Audience

The primary stakeholders are public health officials and policymakers who aim to improve vaccination campaigns and resource allocation. Understanding which factors influence vaccine uptake enables targeted public health interventions and more effective communication strategies.

## Dataset Understanding

The dataset contains self-reported survey responses including:

Demographic information (age group, education level, income)

Health behaviors (mask usage, avoidance behavior)

Opinions and beliefs about H1N1 risk and vaccine effectiveness

The target variable is binary, indicating whether an individual received the H1N1 vaccine. The dataset is imbalanced, with fewer vaccinated individuals, making precision and recall critical evaluation metrics.

## Modeling

The following models were implemented:

Logistic Regression (Baseline)

- Provided a simple and interpretable starting point

- Applied class weighting to handle imbalance

- Achieved high recall for vaccinated individuals but low precision

Tuned Logistic Regression

- Hyperparameters optimized using GridSearchCV

- Precision used as the optimization metric

- Improved precision and overall accuracy at the cost of recall

Decision Tree Classifier

- Captured non-linear relationships in the data

- Simple model struggled to accurately predict vaccinated individuals

Tuned Decision Tree

- Hyperparameters optimized for accuracy

- Improved overall performance and precision

- Recall for the vaccinated class remained limited

Feature importance analysis revealed that perceived risk, belief in vaccine effectiveness, and concern about H1N1 were the most influential predictors, outweighing demographic variables.

## Evaluation

Models were evaluated using:

Accuracy

Precision, Recall, and F1-score

Confusion matrices

## Key Observations

Logistic Regression favored identifying vaccinated individuals (high recall)

Tuned models reduced false positives, increasing precision

Tree-based models better captured complex feature interactions

No single model optimized both precision and recall simultaneously

This highlights an important trade-off between confidence in predictions and coverage of vaccinated individuals.

## Conclusion

This study demonstrates that vaccine uptake is strongly influenced by individual perceptions and behaviors rather than demographics alone. While Logistic Regression offered interpretability and strong baseline performance, tuned models improved prediction confidence by reducing false positives.

The final model selection depends on public health priorities. If the goal is to identify as many vaccinated individuals as possible, higher recall models are preferable. However, if the objective is to make high-confidence predictions, models optimized for precision are more suitable. These findings provide actionable insights for designing targeted vaccination strategies and health communication campaigns.

