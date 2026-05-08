# 🔥 Developer Burnout Prediction

A data-driven machine learning project that analyzes developer lifestyle metrics to predict burnout levels
— helping organizations and individuals identify at-risk patterns early.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Workflow](#workflow)
- [Models](#models)
- [Results](#results)
- [Key Insights](#key-insights)
- [Technologies Used](#technologies-used)

---

## Overview

Burnout is one of the most critical yet overlooked issues in the software industry. 
This project takes a data-driven approach to understand and predict developer burnout levels using real-world-like 
developer lifestyle metrics such as daily work hours, sleep, stress, and exercise habits.

The target variable `burnout_level` is categorized into three levels:

| Label  | Encoded Value |
|--------|--------------|
| Low    | 0            |
| Medium | 1            |
| High   | 2            |

---

## Dataset

| Property        | Details                              |
|----------------|--------------------------------------|
| File            | `developer_burnout_dataset_7000.csv` |
| Rows            | 7,000                                |
| Columns         | 12                                   |
| Numerical       | 11                                   |
| Categorical     | 1 (`burnout_level`)                  |
| Missing Values  | ~140 per column (~2%)                |
| Duplicates      | None                                 |

### Features

- `daily_work_hours` — Average hours worked per day
- `sleep_hours` — Average hours of sleep per night
- `stress_level` — Self-reported stress score
- `exercise_hours` — Weekly exercise hours
- *(and other developer lifestyle metrics)*
- `burnout_level` — **Target variable** (Low / Medium / High)

---

## Project Structure

```
developer-burnout-prediction/
│
├── burnout_with_observations.ipynb      # Notebook 
├── developer_burnout_dataset_7000.csv   # Dataset
└── README.md                            # Project documentation
```

---

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/developer-burnout-prediction.git
   cd developer-burnout-prediction
   ```

2. **Install dependencies**
   ```bash
   pip install numpy pandas seaborn matplotlib scikit-learn missingno
   ```

3. **Launch the notebook**
   ```bash
   jupyter notebook burnout.ipynb
   ```

---

## Workflow

```
Raw Data
   │
   ▼
Data Loading & Inspection
   │  (shape, dtypes, nunique, describe)
   ▼
Missing Value Analysis
   │  (missingno matrix → confirmed MAR pattern)
   ▼
Imputation
   │  (Iterative Imputer with LinearRegression estimator)
   ▼
Label Encoding
   │  (burnout_level: Low→0, Medium→1, High→2)
   ▼
Exploratory Data Analysis
   │  (histograms, pie charts, correlation heatmap, scatter plots, boxplots)
   ▼
Feature / Target Split + Train-Test Split (80/20)
   │
   ▼
Feature Scaling (StandardScaler)
   │
   ▼
Model Training
   │  (Linear Regression, Random Forest, Gradient Boosting)
   ▼
Evaluation (R² Score, MSE)
```

---

## Models

Three regression models are trained and compared:

| Model                     | Type               | Notes                                      |
|--------------------------|--------------------|--------------------------------------------|
| Linear Regression         | Parametric         | Baseline model; assumes linear relationships |
| Random Forest Regressor   | Ensemble (bagging) | Handles non-linearity; robust to noise     |
| Gradient Boosting Regressor | Ensemble (boosting) | Sequential correction; typically highest accuracy |

---

## Results

Models are evaluated using:

- **R² Score** — Proportion of variance explained (higher is better; 1.0 = perfect)
- **MSE** — Mean Squared Error (lower is better)

> Expected ranking: **Gradient Boosting ≥ Random Forest > Linear Regression**

An R² above **0.80** indicates a strong, reliable predictor of developer burnout.

---

## Key Insights

- **Work hours and stress level** are among the strongest positive predictors of burnout.
- **Sleep and exercise** act as protective factors — negatively correlated with burnout.
- Missing values (~2% per column) were scattered across different rows (MAR pattern), making imputation safe and effective.
- No significant outliers were detected — the dataset is clean and well-distributed.
- The three burnout classes are approximately balanced, making accuracy a fair evaluation metric.

---

## Technologies Used


- **Python 3.8+**
- **pandas**, **numpy** — Data manipulation
- **seaborn**, **matplotlib** — Visualization
- **scikit-learn** — Imputation, scaling, modeling, evaluation
- **missingno** — Missing value visualization

---

## Author

> Built as a data science project exploring the intersection of developer wellness and machine learning.
