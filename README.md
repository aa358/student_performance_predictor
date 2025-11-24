# 🎓 Academic Performance Regression Model

Predicting student exam outcomes using machine learning and educational analytics.

## 📌 Purpose

The goal of this project is to build a regression model that predicts a student's final exam grade (G3) using behavioral, academic, and lifestyle features from the UCI Student Performance Dataset.
Beyond prediction accuracy, this project focuses on understanding which factors most influence academic performance, and how data-driven insights can support early intervention for at-risk students.

## 📂 Dataset

* Source: UCI Machine Learning Repository

    * File used: student-mat.csv

    * Samples: 395

    * Target variable: G3 (final grade, 0–20)

The dataset includes categories such as:

* Academic: study time, past grades (G1, G2), absences

* Family/Social: family support, living situation

* Lifestyle: weekday/weekend alcohol use

* Demographic: age, parental education

## 🛠️ Techniques Used

* Data Cleaning & Exploration (EDA)

* Feature Engineering

   * avg_previous_grade = (G1 + G2) / 2

   * Weekalc = (Dalc + Walc) / 2

* One-Hot Encoding for categorical variables

* Feature Scaling with StandardScaler

* Train/Test Split (test_size=0.2, random_state=42)

* Regression Models

   * Baseline: Linear Regression

   * Improved: Polynomial Regression (degree = 2)

* Evaluation Metrics

   * MAE, RMSE, R² score

* Model Diagnostics

   * Correlation heatmap

   * Predictions vs Actual

   * Residual plots

## 🔎 Approach
### 1. Exploratory Data Analysis

   * Inspected dataset structure with .info() and .describe()

   * Checked distributions and missing values

   * Identified key predictors through a correlation heatmap → avg_previous_grade strongly correlated with G3

### 2. Feature Engineering

Created two meaningful features based on domain intuition:

| Feature              | Description                                        |
| -------------------- | -------------------------------------------------- |
| `avg_previous_grade` | Average of G1 and G2 — captures academic trend     |
| `Weekalc`            | Combined alcohol use — lifestyle pattern indicator |


### 3. Preprocessing

   * One-hot encoded categorical columns (schoolsup)

   * Scaled numerical features using StandardScaler

   * Split into training and testing sets before scaling

### 4. Modeling

Trained two models:

   * Baseline Linear Regression

   * Polynomial Regression (degree=2)
Used PolynomialFeatures() to capture mild nonlinearity.


### 5. Evaluation

Evaluated using MAE, RMSE, and R².
(Results are shown below.)

### 6. Visualization

Generated three key plots:

  * Correlation heatmap
<img width="450" height="300" alt="Correlation Heatmap" src="https://github.com/user-attachments/assets/f03bf515-3f2e-4daf-8660-7df66015919a" />

  * Actual vs Predicted scatterplots
<img width="450" height="300" alt="Scatterplot - Baseline" src="https://github.com/user-attachments/assets/ddd0f4c8-4215-4d4e-a659-e1028d3d8d6d" />
<img width="450" height="300" alt="Scatterplot - Polynomial" src="https://github.com/user-attachments/assets/12c82fa7-aa4c-4b95-9c00-4f73635fb385" />

  * Residual plots for error analysis
<img width="450" height="300" alt="Residual Plot - Baseline" src="https://github.com/user-attachments/assets/6970ec0b-ebfb-4489-8bf4-c2c43fd1b11f" />
<img width="450" height="300" alt="Residual Plot - Polynomial" src="https://github.com/user-attachments/assets/eac46bee-ba32-4968-ad2e-4f3e49c77d9b" />

## 📈 Key Insights
### 🔥 Correlation Heatmap

*avg_previous_grade* was by far the strongest predictor of final exam performance.<br>
Alcohol consumption (*Weekalc*) had a mild negative correlation.<br>
Absences and study time showed weak linear relationships.

**Interpretation: Past academic performance matters far more than lifestyle or support features.**

### 🎯 Model Performance
| Model                                | MAE       | RMSE      | R²       |
| ------------------------------------ | ---------- | ---------- | ---------- |
| **Baseline Linear Regression**       | 1.6751     | 2.2543     | 0.7522     |
| **Polynomial Regression (degree=2)** | **1.6076** | **2.2319** | **0.7571** |

The polynomial model offered a small but consistent improvement across all metrics.

### 📊 Predictions vs Actual

Both models predicted well, with the polynomial model producing slightly tighter clustering around the ideal line.

### 🪫 Residual Behavior

Residuals were centered around zero with no strong pattern, indicating:
* No major bias
* Linearity assumptions hold reasonably well
* Mild heteroscedasticity at high grades (common in student datasets)

## 🧪 Final Results

✔ Achieved an R² of ~0.76 on the polynomial model <br>
✔ Predicted final grades within ~1.6 points MAE <br>
✔ Engineered features noticeably improved performance <br>
✔ Past grades dominate prediction strength <br>
✔ Visualization confirmed the model’s reliability and interpretability

## 🧩 Project Value (Portfolio Impact)

This project demonstrates the ability to:

* Work with real-world educational datasets

* Apply practical regression techniques

* Engineer meaningful features from domain knowledge

* Evaluate and compare multiple models

* Create insightful visualizations for interpretability

* Write clean, reproducible ML code

* Explain model behavior clearly and professionally
