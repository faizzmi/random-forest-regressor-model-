<div align="center">

# Random Forest Practice

A self-study project exploring Random Forest for both classification and regression tasks using two classic ML datasets.

[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=flat-square&logo=python)](https://python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-latest-F7931E?style=flat-square&logo=scikit-learn)](https://scikit-learn.org)
[![Status](https://img.shields.io/badge/Status-Learning%20Only-blue?style=flat-square)]()

</div>

---

## Why This Exists

Random Forest is one of the most widely used ML algorithms and I wanted to understand how it actually works beyond just reading about it. This repo is purely for learning — two isolated implementations, one for classification and one for regression, using well-known datasets so results are easy to verify.

---

## What It Does

### Classification — Titanic Survival Prediction

| Step | What Happens |
|---|---|
| Load data | Titanic CSV loaded via pandas, rows with missing target dropped |
| Feature selection | Pclass, Sex, Age, SibSp, Parch, Fare selected as inputs |
| Encoding | Sex mapped to numeric (female = 0, male = 1) |
| Missing values | Age nulls filled with median age |
| Train/test split | 80% train, 20% test, random state 42 |
| Model | RandomForestClassifier with 100 estimators |
| Output | Survived or Did Not Survive per passenger |

### Regression — California Housing Price Prediction

| Step | What Happens |
|---|---|
| Load data | California Housing dataset fetched from sklearn |
| Features | Average income, house age, rooms, location, etc. |
| Train/test split | 80% train, 20% test, random state 42 |
| Model | RandomForestRegressor with 100 estimators |
| Output | Predicted median house value |

---

## Stack

**Language** — Python 3.x

**Libraries** — scikit-learn, pandas, NumPy

**Dataset (Classification)** — Titanic (Kaggle)

**Dataset (Regression)** — California Housing (sklearn built-in)

---

## Project Structure

```
random-forest-practice/
├── classification.py       # Titanic survival prediction
├── regression.py           # California housing price prediction
└── titanic.csv             # Not included, get from Kaggle
```

---

## Running Locally

### Prerequisites

- Python 3.8+
- pip

### Install dependencies

```bash
pip install pandas scikit-learn
```

### Run

```bash
# Classification
python classification.py

# Regression
python regression.py
```

> Titanic dataset not included. Download `titanic.csv` from [Kaggle](https://www.kaggle.com/c/titanic/data) and place it in the root folder.

---

## Results

### Classification — Titanic

| Metric | Score |
|---|---|
| Accuracy | 80% |
| Precision (Not Survived) | 0.82 |
| Precision (Survived) | 0.77 |
| Recall (Not Survived) | 0.85 |
| Recall (Survived) | 0.73 |
| F1 (Not Survived) | 0.83 |
| F1 (Survived) | 0.75 |

Sample prediction — 3rd class male, age 28, fare 15.25: **Did Not Survive**

### Regression — California Housing

| Metric | Score |
|---|---|
| R² Score | 0.81 |
| Mean Squared Error | 0.26 |

Sample prediction — predicted: 0.51, actual: 0.48

---

## What I Learned

- Random Forest averages predictions across many decision trees which reduces overfitting compared to a single tree. More trees = more stable result but slower training
- Feature encoding matters — leaving Sex as a string would cause the model to fail since sklearn expects numeric input
- Filling missing values with the median is safer than the mean for skewed distributions like Age in Titanic
- R² of 0.81 means the model explains 81% of variance in house prices, solid for a baseline with zero hyperparameter tuning
- 100 estimators is a reasonable default but not always optimal — more trees help up to a point then plateau

## What Needs Improving

- No hyperparameter tuning done — `n_estimators`, `max_depth`, `min_samples_split` all left at defaults
- No cross-validation, so reported accuracy could vary depending on the random split
- Feature importance analysis not included — would be useful to see which features actually drive predictions
- No visualisations — confusion matrix, feature importance chart, and residual plots would make results clearer
- Only tested on clean, well-known datasets — would be more useful to try on messier real-world data

---

<div align="center">
Personal learning project. Not production code. Built to understand how Random Forest works by actually running it.
</div>
