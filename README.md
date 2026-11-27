# An Evaluation of Machine Learning Survival Architectures and Competing Risk Frameworks in Cardiovascular Time-to-Event Projections

## Project Overview
Traditional binary classifiers ignore when a heart failure patient dies and treat right-censored follow-up as survival. This project evaluates time-to-event survival architectures—comparing a Kaplan–Meier baseline, Cox Proportional Hazards models (`Cox-2` and `Cox-10`), a Logistic Regression benchmark, Random Survival Forest (`RSF`), and Gradient Boosted Survival (`GBS`)—using 5-fold stratified cross-validation repeated 3 times (15 outer splits, `seed=42`) with nested 3-fold hyperparameter tuning.

## Dataset
* **Source:** [UCI Heart Failure Clinical Records Dataset](https://doi.org) (Chicco & Jurman, 2020)
* **License:** CC BY 4.0
* **Cohort:** 299 patients from Faisalabad, Pakistan (96 deaths / 32.1%, 203 right-censored / 67.9%, follow-up 4–285 days, median 115 days, 0 missing values).
* **Features:** 10 selected clinical predictors (`smoking` dropped due to univariate C-index of 0.506 and correlation \(r = 0.45\) with `sex`).

## Key Findings (Mean over 15 Test Folds)

| Model | C-index | Mean Time-Dependent AUC | Integrated Brier Score (30–180d) |
| :--- | :---: | :---: | :---: |
| **Random Survival Forest (RSF)** | **0.734 ± 0.063** | **0.753** | **0.157 ± 0.018** |
| **Gradient Boosted Survival (GBS)** | 0.731 ± 0.059 | 0.747 | 0.159 ± 0.014 |
| **Cox (10 features)** | 0.710 ± 0.070 | 0.725 | 0.161 ± 0.020 |
| **Logistic Regression** | 0.708 ± 0.077 | 0.722 | n/a |
| **Cox (2 features)** | 0.673 ± 0.083 | 0.666 | 0.172 ± 0.016 |
| **Kaplan–Meier (Baseline)** | 0.500 ± 0.000 | 0.500 | 0.182 ± 0.012 |

* **Top Predictors:** `ejection_fraction`, `serum_creatinine`, and `age` carried almost all predictive signal across both permutation importance and standardised Cox hazard ratios.
* **Competing Risks:** Because the dataset records a single event type (`DEATH_EVENT`) without labelled causes of death, cumulative incidence reduces to \(1 - \text{Kaplan–Meier}\) and multi-event competing-risk models (Fine–Gray, DeepHit) could not be fitted.

## Project Structure
```text
cardiovascular-survival-ml/
├── data/          # Raw and cleaned datasets + CV fold splits
├── notebooks/     # Main Jupyter notebook with EDA, models, and evaluation
├── models/        # Saved final Random Survival Forest model (.joblib)
├── results/       # Evaluation tables and plots
├── report/        # Final 5-page academic PDF report
├── src/           # Auxiliary source scripts
├── README.md      # Project documentation
└── requirements.txt
```

## Setup & Installation
```bash
pip install -r requirements.txt
```
Core libraries: `Python`, `NumPy`, `Pandas`, `Matplotlib`, `Seaborn`, `Scikit-learn (1.9.1)`, `Scikit-survival (0.28.0)`, `Lifelines`, `Joblib`.

## Team Contributions
* **Akshitha Luxetti:** Data collection and cleaning, missing-value checks, EDA visualisations, and cross-validation fold setup.
* **Riya Rajendra Naik:** Kaplan–Meier, Cox regression, and logistic regression models; proportional-hazards assumption checks and risk-factor analysis.
* **Nivedita Divya Rajesh:** Random Survival Forest and Gradient Boosted Survival development, nested tuning, and model comparisons.
* **Gaurang Ajit Shelke:** Report writing, literature review, dataset description, ethics section, bibliography, code testing, and runtime fixes.

## Disclaimer
This project is an educational and retrospective modelling exercise, not a validated clinical decision-support tool.

