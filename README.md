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

Tuning AdaBoost raised its mean cross-validation sensitivity to **0.953**. However, this improvement did not translate into higher held-out sensitivity compared with the default model. The default configuration was therefore retained.

## Software and tools

| Tool | Purpose |
|---|---|
| **KNIME Analytics Platform 5.9** | Data preparation, sampling, feature selection, training, cross-validation, tuning, evaluation and SHAP computation |
| **Python** | Processing the SHAP table exported from KNIME |
| **Jupyter Notebook** | Generating the final SHAP figure |
| **pandas and NumPy** | Tabular and numerical data processing |
| **Matplotlib and Seaborn** | Visualization of the exported results |

## Data source

The analysis uses the [Alzheimer's Disease Dataset](https://www.kaggle.com/datasets/rabieelkharoua/alzheimers-disease-dataset), published on Kaggle by **Rabie El Kharoua**.

It consists of **2,149 synthetic patient records and 35 variables**, including demographics, lifestyle factors, medical history, clinical measurements, cognitive assessments, symptoms and a binary diagnosis label.

The dataset is not distributed with this repository. See [`data/README.md`](data/README.md) for download and setup instructions.

## Repository contents

| Path | Contents |
|---|---|
| `assets/knime_workflow.svg` | Image of the complete KNIME workflow |
| `assets/roc_curves.png` | ROC comparison figure |
| `data/README.md` | Instructions for obtaining and preparing the data |
| `knime/alzheimer_classification_workflow.knwf` | Importable KNIME workflow |
| `notebooks/shap_feature_importance.ipynb` | Auxiliary notebook for the SHAP visualization |
| `report/project_report.pdf` | Full project report |
| `.gitattributes` | Git file-handling settings |
| `.gitignore` | Files and directories excluded from version control |
| `requirements.txt` | Python dependencies for the auxiliary notebook |
| `README.md` | Project description and usage instructions |

## Running the project

### KNIME analysis

1. Download `alzheimers_disease_data.csv` from Kaggle and save it in `data/`.
2. Open KNIME Analytics Platform 5.9.
3. Import `knime/alzheimer_classification_workflow.knwf`.
4. Update the CSV Reader node to use the dataset location on your computer.
5. Adjust the CSV Writer paths if you want to export the correlation matrix or SHAP results.
6. Install any required KNIME extensions when prompted, then execute the workflow.

The workflow is provided in its original submitted form. Input and output paths stored in individual nodes must be checked when moving it to a different computer.

### Optional SHAP visualization

The notebook recreates the formatting of the SHAP figure included in the report. First, export the SHAP table from KNIME to `data/shap_xai_table.csv`.

Create a Python environment:

```bash
python -m venv .venv
```

Activate it on macOS or Linux:

```bash
source .venv/bin/activate
```

Or activate it on Windows using Command Prompt:

```bat
.venv\Scripts\activate
```

Install the dependencies and open the notebook:

```bash
pip install -r requirements.txt
jupyter notebook notebooks/shap_feature_importance.ipynb
```

## Limitations and interpretation

- **Synthetic data:** the reported results describe performance on this dataset and do not establish clinical validity.
- **SHAP aggregation:** the submitted visualization sums signed SHAP values across observations. It represents net directional contributions. Conventional global SHAP importance typically uses mean absolute values, avoiding cancellation between positive and negative contributions.
- **Original materials:** the workflow, report and experimental results have been preserved. In the notebook, the original absolute file path was replaced with a relative repository path to improve portability.

## Authors and academic context

Developed jointly by:

- [Davide Francesco Caramia](https://github.com/davidecaramia)
- [Nicolò Bachiorri](https://github.com/nicolobachiorri)
- [Hervé Mottaran](https://github.com/hervemottaran)

All three authors contributed across data preparation, workflow development, experimental design, model evaluation, interpretation and presentation.

**Machine Learning Project for Data Science**  
**Università degli Studi di Milano-Bicocca — Academic Year 2025/2026**
