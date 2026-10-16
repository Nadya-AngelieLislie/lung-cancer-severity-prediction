# Lung Cancer Severity Prediction with Machine Learning

> Which factors drive lung cancer severity, and can five classifiers predict it?

## Overview

- Computational biology group project: find which lifestyle, environmental, genetic and symptom factors are significantly related to lung cancer severity (low, medium, high) and predict severity with machine learning.

## Data / Scope

- Kaggle "Lung Cancer Prediction" dataset: 1,000 patients, 23 features (demographic, lifestyle, environment, genetic and symptoms) and a 3-level severity target.
- Split 70/30 (700 training, 300 test); the dataset file is not included.

## Workflow

- EDA: severity distribution, correlation of every feature with severity, age distribution.
- Statistical testing: Chi-square for categorical factors and Kruskal-Wallis for age against severity.
- Models: Logistic Regression, Decision Tree, Random Forest, SVM and KNN, evaluated with classification reports and cross-validation.
- Feature importance from the Random Forest.

## Results

- Every factor except Gender was significantly related to severity (Chi-square p < 0.05; Kruskal-Wallis for age p = 0.0006).
- Strongest links by Chi-square: coughing of blood, alcohol use, passive smoking, obesity and smoking.
- Random Forest, Decision Tree and KNN reached 100% test accuracy and SVM about 97% in the notebook.
- Top Random Forest features: passive smoker, obesity and alcohol use; top symptoms: coughing of blood, chest pain and wheezing.

## Tech Stack

Python, pandas, scikit-learn (chi2, models), seaborn, Matplotlib

## Repository Structure

```
notebook/   Analysis notebook with outputs
docs/       Presentation slides (cover page removed)
figures/    Charts from the presentation
```

## How to Run

```bash
pip install pandas numpy scikit-learn seaborn matplotlib jupyter
jupyter notebook notebook/Lung_Cancer_Severity_Prediction.ipynb
```

Place `cancer patient data sets.csv` (Kaggle) next to the notebook first.

## Team

Group project by Aaron Jeremy Alexander, Amanda Sugito, Kelvin Fardiman, Nadya Angelie Lislie and Nusantara Kusuma (Computational Biology, BINUS University).

## Notes

- Perfect scores suggest this dataset is very easy to separate, so the accuracy numbers should be read with caution rather than as clinical performance.
- The final comparison chart in the presentation shows Logistic Regression at about 0.75 and SVM at about 0.9, which differs from the notebook output (about 1.00 and 0.97); the presentation likely used a different feature set or settings. Re-run to confirm before quoting either.
- The presentation PDF is about 16 MB.
- Course: Computational Biology (inferred from the project file name; please confirm).

## Author

Nadya Angelie Lislie, BINUS University (Computer Science and Statistics). [LinkedIn](https://www.linkedin.com/in/nadya-angelie-lislie/) | [GitHub](https://github.com/Nadya-AngelieLislie)

## Experiment Tracking

`src/experiment_tracking.py` provides an optional MLflow wrapper (`track_run`) for logging parameters, metrics and artifacts; it does nothing when MLflow is not installed. Run `mlflow ui` after logging runs to compare experiments.

## Continuous Integration

GitHub Actions (`.github/workflows/ci.yml`) runs `ruff` and `pytest` repository-health checks on every push; run them locally with `make lint test`.
