
# Machine Learning Survival Models and Competing Risks in Cardiovascular Risk Prediction

## Project Overview

This project aims to evaluate different Machine Learning survival architectures and competing risk frameworks for predicting the timing of cardiovascular events.

Traditional binary classification methods often fail to account for censored clinical data and the time at which an event occurs. This project explores survival analysis techniques to model time-to-event outcomes more effectively.

## Problem Statement

Predicting whether a cardiovascular event will occur is not always sufficient. Understanding when the event may occur is also important for clinical risk assessment.

This project investigates survival-based approaches to address this challenge.

## Objectives

- Explore Machine Learning survival analysis techniques.
- Evaluate different survival model architectures.
- Investigate competing risk frameworks.
- Analyse censored time-to-event clinical data.
- Study the contribution of clinical biomarkers such as ejection fraction and serum creatinine.
- Compare model performance using appropriate survival evaluation metrics.

## Proposed Approach

The project aims to use clinical data, data preprocessing, survival modelling and model evaluation to investigate cardiovascular time-to-event prediction.

## Dataset

The project will use clinical cardiovascular data containing relevant patient information and biomarkers, including ejection fraction and serum creatinine.

The dataset will be used to investigate time-to-event outcomes and censored observations. Dataset details and licensing information will be documented during implementation.

## Project Structure

```text
cardiovascular-survival-ml/
│
├── data/          # Dataset storage
├── notebooks/     # Jupyter notebooks and experiments
├── src/           # Python source code
├── models/        # Trained machine learning models
├── results/       # Evaluation results and visualisations
├── report/        # Project documentation
├── README.md      # Project overview
├── requirements.txt
└── .gitignore
```

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- SciPy
- Lifelines
- Jupyter Notebook

## Expected Outcomes

- Comparison of different survival model architectures.
- Evaluation of competing risk frameworks.
- Better understanding of cardiovascular time-to-event prediction.
- Identification of suitable approaches for handling censored clinical data.

## Project Status

Currently under development.

## Team Contributions

This is a collaborative Machine Learning project. Team members will contribute to data preparation, model development, experimentation, evaluation and documentation.

## Disclaimer

This project is intended for academic and research purposes only. It is not designed to replace professional medical diagnosis or clinical decision-making.
