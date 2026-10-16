# Alzheimer Disease Classification - ML project
**A comparative study of 11 classification algorithms using synthetic health records.**

## Introduction
This project investigates how different machine learning models perform on a binary Alzheimer's disease classification task. The analysis uses demographic, lifestyle, medical and cognitive information from a synthetic dataset.

The main pipeline was developed in **KNIME Analytics Platform 5.9**, covering data preparation, feature selection, model comparison, hyperparameter optimization and interpretation. **Python and Jupyter** were used for the final formatting of the SHAP visualization.

The work was completed as an academic project. Since the observations are synthetic, the findings should not be interpreted as evidence of clinical diagnostic performance.

## Experimental approach
The study compares 11 classifiers within a shared evaluation framework. **Sensitivity** is the main criterion for selecting a model, reflecting the project's emphasis on reducing false negatives. Accuracy and ROC AUC are also reported to provide a broader assessment of predictive performance.

The workflow covers the following stages:
1. Preparation of demographic, lifestyle, clinical and cognitive variables.
2. A stratified 70/30 training–test split with a fixed random seed.
3. Downsampling of the majority class within the training partition.
4. Z-score normalization fitted on training data.
5. Supervised feature selection.
6. Model comparison through 10-fold cross-validation.
7. Hyperparameter tuning of the selected classifier.
8. Evaluation on the held-out test set and SHAP-based interpretation.

## Workflow
The complete KNIME pipeline brings together preprocessing, class balancing, feature selection, training, evaluation and explainability.

The importable workflow is available in **knime/alzheimer_classification_workflow.knwf**.

## Model comparison
**AdaBoost** obtained the highest average cross-validation sensitivity and was selected as the final classifier. Its held-out test accuracy was **92.6%**, with a **ROC AUC of 0.920**.

**Bagging** achieved the highest test accuracy and ROC AUC. This highlights how the preferred model can change depending on the evaluation metric used.

| Classifier | Mean CV sensitivity | Test accuracy | Test ROC AUC |
|---|---:|---:|---:|
| **AdaBoost** | **0.932** | 0.926 | 0.920 |
| Naive Bayes | 0.924 | 0.932 | 0.922 |
| Bayesian Network | 0.924 | 0.932 | 0.922 |
| Bagging | 0.921 | **0.936** | **0.925** |
| Tree-Augmented Naive Bayes | 0.920 | 0.930 | 0.920 |
| Decision Tree | 0.913 | 0.932 | 0.922 |
| Gradient Boosting | 0.911 | 0.921 | 0.915 |
| Random Forest | 0.884 | 0.932 | 0.920 |
| Multilayer Perceptron | 0.818 | 0.833 | 0.819 |
| Logistic Regression | 0.787 | 0.825 | 0.819 |
| Support Vector Machine | 0.679 | 0.732 | 0.720 |
