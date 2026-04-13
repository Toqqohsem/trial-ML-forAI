# Student Performance Prediction

This project builds a machine learning model to predict whether a student is likely to **pass or fail** a course based on demographic, academic, and behavioral factors. It combines two datasets (Math and Portuguese) from the UCI Machine Learning Repository to analyze key performance indicators and support early intervention in education.

---

## 🔍 Objective

The goal is to develop a **binary classification model** that predicts student success (Pass = 1, Fail = 0) and provides **interpretable insights** into which features influence outcomes the most.

---

## 📦 Dataset

- Source: [UCI Student Performance Dataset](https://archive.ics.uci.edu/ml/datasets/Student+Performance)
- Files used:
  - `student-mat.csv` – Math performance
  - `student-por.csv` – Portuguese performance
- Merged on shared student attributes (school, age, family background, etc.)
- New feature: `G3_avg` = average of both final grades, used to create the target variable

---

## 🛠️ Tools & Libraries

- Python, Pandas, NumPy
- Scikit-learn
- Matplotlib, Seaborn
- SHAP, LIME (Model Explainability)
- SMOTE (for oversampling)
- GridSearchCV (Hyperparameter Tuning)

---

## 🧪 Methodology

### 1. Data Preprocessing
- Merged Math and Portuguese datasets
- Encoded categorical features
- Removed final grade columns to avoid data leakage
- Created new features such as `studytime * failures`, `absences / age`

### 2. Exploratory Data Analysis (EDA)
- Analyzed target distribution, correlations, and feature relationships
- Identified key factors: study time, absences, failures, alcohol use, internet access

### 3. Model Building
- Trained Logistic Regression, Decision Tree, and Random Forest classifiers
- Handled class imbalance using:
  - `class_weight='balanced'`
  - SMOTE (optional)
- Tuned hyperparameters with GridSearchCV

### 4. Threshold Tuning
- Evaluated prediction probabilities and tested thresholds from 0.3 to 0.7
- Selected optimal threshold of **0.30** for **maximizing overall accuracy and Pass class prediction confidence**

### 5. Model Explainability
- SHAP: Visualized global feature importance
- LIME: Explained individual predictions

---

## 📊 Final Model Performance (Threshold = 0.30)

| Metric        | Value     |
|---------------|-----------|
| Accuracy      | 75.3%     |
| Recall (Fail) | 5.0%      |
| F1 (Fail)     | 9.5%      |
| Recall (Pass) | 100.0%    |
| F1 (Pass)     | 85.7%     |

---

## 🧠 Key Insights

- **Absences, failures, low study time, and weekend alcohol use** are strong predictors of failure.
- **School support, parental education, and internet access** contribute positively to performance.
- Threshold tuning improved the model’s ability to **predict passes with high confidence**, though fail cases remain under-detected at this threshold.

---

## 📂 Repository Structure

```
student-performance-prediction/
├── data/
│   ├── student-mat.csv
    ├── student.txt
    ├── student-merge.r
    ├── .student.zip_old.zip
│   └── student-por.csv
├── notebooks/
│   └── student_performance_model.ipynb
├── docs/
│   ├── Executive_Summary.docx
├── README.md
```

## 📬 Contact

For queries, collaboration, or feedback, feel free to reach out  via GitHub or email.

---

