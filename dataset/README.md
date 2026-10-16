The dataset must be downloaded separately, as it is not provided in this repository.

- Obtain **alzheimers_disease_data.csv** from the Alzheimer's Disease Dataset on Kaggle.
- Save the downloaded file in the **data/** folder before opening the KNIME workflow.

If you plan to run the optional SHAP notebook, this folder must also contain **shap_xai_table.csv**. Generate this file by exporting the results from the SHAP branch of the KNIME workflow.

Once the required files have been added, the folder should contain:

- **alzheimers_disease_data.csv** — input dataset.
- **shap_xai_table.csv** — exported SHAP results, needed only for the optional notebook.
- **README.md** — instructions for preparing the data files.
