# Reference Repository Inventory

This document catalogs the 4 trial/reference repositories in this workspace, what they contain, and how they map to our AIM 2602 assignment.

---

## 1. KNN-vs-Decision-Trees/

**Source:** External reference (UCI ML Repository datasets)
**Relevance:** HIGH — directly compares our two target algorithms

### Contents
| File | Purpose |
|------|---------|
| `KNN_DecisionTrees.ipynb` | Full notebook comparing KNN vs Decision Tree |
| `adult/adult.data`, `adult/adult.test` | UCI Adult dataset (census income classification) |
| `bank/bank.csv`, `bank/bank-full.csv` | UCI Bank Marketing dataset |
| `roc_comparison.png` | ROC curve comparison output |

### Key Takeaways for Our Project
- **Methodology:** 5-fold cross-validation, growing training subsets, hyperparameter tuning
- **Finding:** KNN achieved worse accuracy than DT and was significantly slower (43 min vs 1 min)
- **KNN best:** K=12, accuracy 0.84 on validation
- **DT best:** max_depth=7, accuracy 0.87 on validation
- **Lesson:** DT outperformed KNN on these tabular datasets; document computational cost difference

### What We Can Reuse
- Cross-validation approach
- Hyperparameter sweep methodology
- ROC curve comparison technique
- Accuracy vs hyperparameter plotting

---

## 2. Student-Performance-Prediction/

**Source:** External reference (UCI Student Performance — Paulo Cortez)
**Relevance:** HIGH — same domain (student performance), same dataset option

### Contents
| File | Purpose |
|------|---------|
| `Notebook/Student_Performance_Prediction.ipynb` | Main notebook |
| `Notebook/Student_Performance_Prediction_local.ipynb` | Local variant |
| `Notebook/executed_output.ipynb` | Pre-executed output |
| `Data/student-mat.csv` | Math performance data |
| `Data/student-por.csv` | Portuguese performance data |
| `Data/student-merge.R` | R script for merging datasets |
| `Data/student.txt` | Dataset description |
| `Docs/Executive_Summary.docx` | Executive summary document |

### Key Takeaways for Our Project
- **Models used:** Logistic Regression, Decision Tree, Random Forest (we only need DT + KNN)
- **Preprocessing:** Merged Math + Portuguese datasets, created `G3_avg`, encoded categoricals
- **Advanced features:** SHAP + LIME for explainability, SMOTE for class imbalance, GridSearchCV
- **Result:** 75.3% accuracy at threshold 0.30
- **Lesson:** Class imbalance is a real issue; threshold tuning matters; feature engineering adds value

### What We Can Reuse
- UCI dataset preprocessing approach
- Feature engineering ideas (`studytime * failures`, `absences / age`)
- Confusion matrix and classification report patterns
- EDA structure and visualization approach

---

## 3. bernaibrahimli-student-prediction/

**Source:** External reference (UCI Student Performance)
**Relevance:** MEDIUM — Decision Tree specific, same dataset

### Contents
| File | Purpose |
|------|---------|
| `prediction_model.ipynb` | Decision Tree model notebook |
| `executed_output.ipynb` | Pre-executed output |

### Key Takeaways for Our Project
- **Model:** Decision Tree only (no KNN comparison)
- **Dataset:** UCI Student Performance (same as #2)
- **Lesson:** Simpler implementation, good for understanding DT basics

### What We Can Reuse
- Decision Tree implementation pattern
- Basic preprocessing for UCI student data

---

## 4. student-performance-prediction/

**Source:** External reference (Kaggle xAPI-Edu-Data)
**Relevance:** HIGH — uses our alternative dataset, online learning behavior angle

### Contents
| File | Purpose |
|------|---------|
| `machine_learning_model.ipynb` | ML model notebook |
| `executed_output.ipynb` | Pre-executed output |
| `data.csv` | xAPI-Edu-Data (480 records, 16 features) |
| `documentation.docx` | Documentation |

### Key Takeaways for Our Project
- **Dataset:** Kaggle xAPI-Edu-Data — behavioral indicators (raised hands, visited resources, discussion participation)
- **Angle:** Online learning behavior analytics
- **Requirements overlap:** Matches our assignment's CLO requirements exactly
- **Lesson:** Behavioral features may be more predictive than demographic ones

### What We Can Reuse
- xAPI-Edu-Data preprocessing
- Online learning behavior framing (useful for JATI journal angle)
- Feature dimension/indicator analysis

---

## Summary: Which References Map to Which Parts of Our Assignment

| Assignment Section | Best Reference(s) |
|--------------------|--------------------|
| Data preprocessing | #2 (Student-Performance-Prediction), #4 (student-performance-prediction) |
| Decision Tree implementation | #1 (KNN-vs-Decision-Trees), #3 (bernaibrahimli) |
| KNN implementation | #1 (KNN-vs-Decision-Trees) |
| Hyperparameter tuning | #1 (KNN-vs-Decision-Trees), #2 (GridSearchCV) |
| Model comparison methodology | #1 (KNN-vs-Decision-Trees) |
| Visualizations | #1 (ROC curves), #2 (confusion matrices, SHAP) |
| Feature importance | #2 (SHAP/LIME) |
| Dataset choice | #4 for xAPI-Edu-Data, #2 for UCI |

---

*Status: DRAFT — Reference for team use during development*
