# Claude Code Context — AIM 2602 Group Assignment

## PROJECT OVERVIEW

This is a university group assignment for **AI Methods (CT002-3-2)** at Asia Pacific University (APU).
The task is to implement an AI algorithm in Python, demonstrate it via simulation, and document it in JATI journal format.

**Module:** AIM 2602 — AI Methods
**Lecturer:** Zailan Arabee bin Abdul Salam
**Deadlines:**
- Week 8 (27 April 2026): Simulation code presentation — run the algorithm, explain the problem/approach, report results
- Week 14 (12 June 2026): Final documentation submission + presentation

---

## PROBLEM STATEMENT

**Student Performance Prediction Using Machine Learning**

Predict whether a student will **pass or fail** (binary classification) based on features such as study hours, attendance, parental education, etc.

**Approach:**
- Compare **two classification models**: Decision Tree and K-Nearest Neighbors (KNN)
- Modify/tune hyperparameters for each model and analyze how results change
- Evaluate using metrics like accuracy, precision, recall, F1-score, and confusion matrix

---

## REFERENCE ALGORITHM / SOURCE CODE

Use the publicly available repository as a reference base:
- **Primary reference:** https://github.com/JLongLew/student-performance-prediction
  - Uses KNN, Decision Tree, SVM, Logistic Regression on student performance data
  - Dataset: Kaggle xAPI-Edu-Data (https://www.kaggle.com/datasets/aljarah/xAPI-Edu-Data)
- **Alternative reference:** https://github.com/mohammedAljadd/students-performance-prediction
  - Predicts pass/fail using KNN, Logistic Regression, SVM
  - Dataset: UCI Student Performance (Paulo Cortez, University of Minho)

You may use either dataset. The Kaggle xAPI-Edu-Data has 480 student records with 16 features including behavioral indicators. The UCI dataset has features like study time, absences, family background, and past grades.

---

## WHAT TO BUILD

### 1. Data Loading & Preprocessing
- Load the dataset (CSV)
- Handle missing values if any
- Encode categorical variables (Label Encoding or One-Hot Encoding)
- Feature selection — identify the most relevant features
- Split data into training set (80%) and test set (20%)
- Normalize/standardize features where appropriate (especially for KNN)

### 2. Model 1: Decision Tree Classifier
- Train a Decision Tree using scikit-learn
- Experiment with hyperparameters:
  - `max_depth`: try values [3, 5, 7, 10, None]
  - `criterion`: try ['gini', 'entropy']
  - `min_samples_split`: try [2, 5, 10]
- Visualize the decision tree
- Record accuracy, precision, recall, F1-score for each configuration

### 3. Model 2: K-Nearest Neighbors (KNN) Classifier
- Train a KNN model using scikit-learn
- Experiment with hyperparameters:
  - `n_neighbors` (K): try values [3, 5, 7, 9, 11]
  - `weights`: try ['uniform', 'distance']
  - `metric`: try ['euclidean', 'manhattan']
- Plot accuracy vs. K value graph
- Record accuracy, precision, recall, F1-score for each configuration

### 4. Model Comparison & Evaluation
- Generate confusion matrices for both models (best configuration each)
- Classification report (precision, recall, F1 per class)
- ROC curves if applicable
- Side-by-side comparison table of best Decision Tree vs best KNN
- Cross-validation (e.g., 5-fold or 10-fold) for more robust evaluation
- Feature importance analysis (Decision Tree provides this natively)

### 5. Visualizations (Important for Presentation)
- Confusion matrix heatmaps for both models
- Accuracy vs hyperparameter plots (K value for KNN, max_depth for DT)
- Decision Tree visualization (tree diagram)
- Feature importance bar chart
- ROC curves comparison
- Optional: correlation heatmap of features

---

## TECHNICAL REQUIREMENTS

- **Language:** Python 3
- **Environment:** Jupyter Notebook (.ipynb)
- **Required Libraries:** pandas, numpy, scikit-learn, matplotlib, seaborn
- **Optional Libraries:** graphviz (for tree visualization)
- Code must be **well-commented** — each section should explain what it does and why
- Code must be **fully executable** — the lecturer will run it during presentation

---

## OUTPUT STRUCTURE

Organize the Jupyter Notebook with these clearly labeled sections:

```
1. Introduction & Problem Statement
2. Dataset Description
3. Data Loading & Exploration (EDA)
4. Data Preprocessing
5. Model 1: Decision Tree
   5.1 Training with default parameters
   5.2 Hyperparameter tuning
   5.3 Results & evaluation
6. Model 2: KNN
   6.1 Training with default parameters
   6.2 Hyperparameter tuning
   6.3 Results & evaluation
7. Model Comparison
   7.1 Side-by-side metrics table
   7.2 Confusion matrices
   7.3 ROC curves
   7.4 Cross-validation results
8. Feature Importance Analysis
9. Conclusion & Recommendations
```

---

## GRADING CRITERIA (What the Lecturer Looks For)

For **75% and above**, the project must demonstrate:
- Thorough documentation and complete coverage of the problem area
- Ability to **critically evaluate** the algorithms — not just run them, but explain WHY one performs better
- Sound understanding of the algorithms and how parameters affect results
- Systematic approach to explanation and evaluation
- Extensive critical insight — e.g., discussing overfitting, bias-variance tradeoff, when DT is better vs KNN

For the **Week 8 code presentation**, each group member must present one of:
- A portion of the algorithm implementation
- The relevant parameters/approach taken
- The results of the output
- Suggestions for future work or improvements

---

## IMPORTANT NOTES

- This is a **group assignment** — the code and documentation should reflect collaborative work, not one person per section
- The final documentation must follow the **JATI Journal Article template** format (max 10 pages)
- The code should be sourced from existing public algorithms but adapted and extended — not just copy-pasted
- At least **2 JATI papers** must be cited in the final documentation
- All code must be submitted as softcopy in a zipped file