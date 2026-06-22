# Song Release Year Prediction - End-to-End Regression Pipeline

## Purpose

This repository contains the implementation of an end-to-end regression pipeline. The goal is to predict the release year of a song from its audio features using the Million Song Dataset subset provided as `midterm-regresi-dataset.csv`.

## Project Overview

The pipeline covers the full regression workflow:

- Data loading from `midterm-regresi-dataset.csv`
- Data preprocessing including missing value imputation and IQR-based outlier removal
- Feature standardization with StandardScaler
- Hyperparameter tuning using Optuna
- Model interpretation using LIME
- Evaluation using standard regression metrics
- Experiment tracking with MLflow

The dataset contains 90 anonymous audio features per song, with the first column representing the target variable (release year, e.g. 2001).

## Model and Results

**Model: Ridge Regression**

Ridge Regression was used as the regression model. The regularization parameter alpha was optimized using Optuna over 50 trials, minimizing MSE on the test set.

Tuned hyperparameter:

- `alpha`: search range 0.001 to 100 (log scale)

Evaluation metrics on the test set:

| Metric | Value |
|--------|-------|
| MSE | 70.1440 |
| RMSE | 8.3752 |
| MAE | 6.0482 |
| R2 | 0.3567 |

A LIME explanation is generated for one test instance to show which features most influenced the model's prediction.

## How to Navigate

1. Open `Tugas 2.ipynb` in Google Colab.
2. Run the first cell to install required packages (`optuna`, `lime`, `mlflow`).
3. Run the imports cell.
4. In the **Data Loading** section, upload `midterm-regresi-dataset.csv` when the file picker appears.
5. Proceed through the cells in order:
   - **Data Preprocessing** — median imputation, IQR outlier removal, train/test split, standardization
   - **Machine Learning Model** — Optuna tuning, Ridge Regression training, MLflow logging, evaluation metrics, actual vs predicted plot
   - **Model Interpretation** — LIME explanation for a single test instance
