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
