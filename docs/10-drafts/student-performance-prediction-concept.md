# Product Concept: Student Performance Prediction Using ML

## Problem Statement

Educational institutions lack early-warning mechanisms to identify students at risk of academic failure. Manual identification is slow, subjective, and often too late for effective intervention. A data-driven approach using machine learning can predict student outcomes based on measurable factors, enabling timely support.

## Proposed Solution

Build a **binary classification system** that predicts whether a student will **pass or fail** by comparing two ML algorithms — **Decision Tree** and **K-Nearest Neighbors (KNN)** — with systematic hyperparameter tuning and evaluation.

## Key Features

- Data preprocessing pipeline (encoding, normalization, feature selection)
- Decision Tree classifier with hyperparameter experiments (max_depth, criterion, min_samples_split)
- KNN classifier with hyperparameter experiments (n_neighbors, weights, metric)
- Side-by-side model comparison (accuracy, precision, recall, F1-score)
- Confusion matrix heatmaps, ROC curves, feature importance charts
- Cross-validation for robust evaluation
- Critical analysis of when/why each algorithm performs better

## Target Users

- **Primary:** Lecturer (Zailan Arabee bin Abdul Salam) — for grading
- **Academic:** AIM 2602 AI Methods course, APU
- **Conceptual:** Educational administrators seeking early intervention tools

## Success Metrics

- Both models fully implemented and tunable
- Clear visual comparison of model performance
- Critical evaluation explaining WHY one model outperforms the other
- Achieves 75%+ grading tier (thorough documentation + critical insight)
- Fully executable Jupyter notebook for Week 8 presentation (27 April 2026)
- Final JATI journal documentation for Week 14 (12 June 2026)

## Dataset Options

| Dataset | Source | Records | Features | Notes |
|---------|--------|---------|----------|-------|
| xAPI-Edu-Data | Kaggle (aljarah) | 480 | 16 | Behavioral indicators (raised hands, visited resources, discussion) |
| UCI Student Performance | UCI (Paulo Cortez) | 395+649 | 30+ | Demographics, grades, family background, alcohol use |

## Reference Repositories (Trial Code)

| Directory | What It Covers | Relevance |
|-----------|---------------|-----------|
| `KNN-vs-Decision-Trees/` | KNN vs DT on adult/bank datasets | Direct algorithm comparison methodology |
| `Student-Performance-Prediction/` | LR, DT, RF on UCI student data with SHAP/LIME | Preprocessing pipeline, explainability approach |
| `bernaibrahimli-student-prediction/` | Decision Trees on UCI student data | DT-specific implementation reference |
| `student-performance-prediction/` | ML model on xAPI-Edu-Data | Kaggle dataset usage, online learning behavior angle |

## Constraints

- Language: Python 3, Jupyter Notebook
- Libraries: pandas, numpy, scikit-learn, matplotlib, seaborn, graphviz
- Must compare exactly 2 models (Decision Tree + KNN)
- Code must be fully executable by lecturer
- Final doc: JATI Journal format, max 10 pages, cite 2+ JATI papers

---

*Status: DRAFT — Awaiting human review before proceeding to full spec (20-specs/)*
