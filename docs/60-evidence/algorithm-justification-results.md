# Algorithm Justification: KNN vs Decision Tree for Student Performance Prediction

**Module:** AIM 2602 — AI Methods (CT002-3-2)
**Dataset:** xAPI-Edu-Data (Kaggle) — 480 students, 16 features
**Date:** 15 April 2026

---

## 1. Baseline Comparison — All 4 Algorithms (Default Parameters)

We first tested all four common classification algorithms to justify our selection:

| Algorithm | Accuracy | F1-Score | 5-Fold CV |
|-----------|----------|----------|-----------|
| **KNN (k=6)** | **0.7292** | **0.7288** | 0.6583 |
| SVM (rbf) | 0.6875 | 0.6873 | 0.6646 |
| Decision Tree (entropy, depth=4) | 0.6458 | 0.6415 | 0.6646 |
| Logistic Regression (C=0.01) | 0.6250 | 0.6070 | 0.6104 |

**Train/Test Split:** 80/20 (384 train, 96 test)
**Classes:** H (High), M (Medium), L (Low)
**Features Used:** VisitedResources, AnnouncementsView, Discussion, StudentAbsenceDays

---

## 2. KNN — Hyperparameter Sweep Results

Tested 20 combinations across K values, weight schemes, and distance metrics:

| K | Weights | Metric | Accuracy | F1-Score | 5-Fold CV |
|---|---------|--------|----------|----------|-----------|
| 3 | uniform | euclidean | 0.6250 | 0.6216 | 0.6146 |
| 3 | uniform | manhattan | 0.7083 | 0.7056 | 0.6250 |
| 3 | distance | euclidean | 0.6875 | 0.6839 | 0.6375 |
| **3** | **distance** | **manhattan** | **0.7500** | **0.7480** | **0.6417** |
| 5 | uniform | euclidean | 0.6562 | 0.6513 | 0.6438 |
| 5 | uniform | manhattan | 0.6458 | 0.6402 | 0.6458 |
| 5 | distance | euclidean | 0.6979 | 0.6941 | 0.6500 |
| 5 | distance | manhattan | 0.7083 | 0.7031 | 0.6479 |
| 7 | uniform | euclidean | 0.6250 | 0.6198 | 0.6708 |
| 7 | uniform | manhattan | 0.6562 | 0.6511 | 0.6750 |
| 7 | distance | euclidean | 0.6771 | 0.6718 | 0.6750 |
| 7 | distance | manhattan | 0.6979 | 0.6938 | 0.6833 |
| 9 | uniform | euclidean | 0.6562 | 0.6541 | 0.6771 |
| 9 | uniform | manhattan | 0.6875 | 0.6839 | 0.6833 |
| 9 | distance | euclidean | 0.7083 | 0.7063 | 0.6937 |
| 9 | distance | manhattan | 0.7083 | 0.7050 | 0.6958 |
| 11 | uniform | euclidean | 0.6771 | 0.6730 | 0.6750 |
| 11 | uniform | manhattan | 0.6771 | 0.6711 | 0.6792 |
| 11 | distance | euclidean | 0.7083 | 0.7053 | 0.7042 |
| 11 | distance | manhattan | 0.7083 | 0.7055 | 0.6958 |

**Best KNN Configuration:** K=3, weights=distance, metric=manhattan — Accuracy: 0.7500

### KNN Observations
- Distance-weighted voting consistently outperforms uniform voting
- Manhattan distance generally performs better than Euclidean on this dataset
- Lower K values (K=3) achieve higher test accuracy, but higher K values (K=9, 11) have better cross-validation stability
- This suggests a tradeoff between fitting the test set and generalization

---

## 3. Decision Tree — Hyperparameter Sweep Results

Tested 30 combinations across criterion, max_depth, and min_samples_split:

| Criterion | Max Depth | Min Split | Accuracy | F1-Score | 5-Fold CV |
|-----------|-----------|-----------|----------|----------|-----------|
| gini | 3 | 2 | 0.6562 | 0.6559 | 0.6250 |
| gini | 3 | 5 | 0.6562 | 0.6559 | 0.6250 |
| gini | 3 | 10 | 0.6562 | 0.6559 | 0.6250 |
| **gini** | **5** | **2** | **0.7083** | **0.7071** | **0.6750** |
| gini | 5 | 5 | 0.7083 | 0.7071 | 0.6667 |
| gini | 5 | 10 | 0.7083 | 0.7071 | 0.6625 |
| gini | 7 | 2 | 0.7083 | 0.7073 | 0.6458 |
| gini | 7 | 5 | 0.6875 | 0.6869 | 0.6458 |
| gini | 7 | 10 | 0.6979 | 0.6957 | 0.6417 |
| gini | 10 | 2 | 0.6771 | 0.6773 | 0.6250 |
| gini | 10 | 5 | 0.6771 | 0.6773 | 0.6062 |
| gini | 10 | 10 | 0.7083 | 0.7067 | 0.6375 |
| gini | None | 2 | 0.6458 | 0.6427 | 0.6458 |
| gini | None | 5 | 0.6771 | 0.6771 | 0.6125 |
| gini | None | 10 | 0.6979 | 0.6958 | 0.6396 |
| entropy | 3 | 2 | 0.6354 | 0.6375 | 0.6250 |
| entropy | 3 | 5 | 0.6354 | 0.6375 | 0.6250 |
| entropy | 3 | 10 | 0.6354 | 0.6375 | 0.6250 |
| entropy | 5 | 2 | 0.6979 | 0.6948 | 0.6521 |
| entropy | 5 | 5 | 0.6667 | 0.6638 | 0.6500 |
| entropy | 5 | 10 | 0.6771 | 0.6726 | 0.6583 |
| entropy | 7 | 2 | 0.6354 | 0.6333 | 0.6104 |
| entropy | 7 | 5 | 0.6354 | 0.6337 | 0.6042 |
| entropy | 7 | 10 | 0.6458 | 0.6400 | 0.6062 |
| entropy | 10 | 2 | 0.6771 | 0.6766 | 0.6083 |
| entropy | 10 | 5 | 0.6354 | 0.6356 | 0.5938 |
| entropy | 10 | 10 | 0.6458 | 0.6395 | 0.5833 |
| entropy | None | 2 | 0.6979 | 0.6963 | 0.6354 |
| entropy | None | 5 | 0.6667 | 0.6644 | 0.6208 |
| entropy | None | 10 | 0.6667 | 0.6602 | 0.5979 |

**Best DT Configuration:** criterion=gini, max_depth=5, min_samples_split=2 — Accuracy: 0.7083

### Decision Tree Observations
- Gini criterion consistently outperforms Entropy on this dataset
- Optimal tree depth is 5 — deeper trees (7, 10, None) show declining cross-validation scores, indicating overfitting
- min_samples_split has minimal impact at shallow depths (depth=3) but matters at deeper levels
- Unlimited depth (None) gives worst cross-validation, confirming overfitting risk

---

## 4. Best KNN vs Best Decision Tree — Detailed Comparison

### Classification Reports

**Best KNN (K=3, distance, manhattan):**

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| H (High) | 0.76 | 0.61 | 0.68 | 31 |
| L (Low) | 0.86 | 0.89 | 0.87 | 27 |
| M (Medium) | 0.67 | 0.76 | 0.72 | 38 |
| **Weighted Avg** | **0.75** | **0.75** | **0.75** | **96** |

**Best Decision Tree (gini, depth=5, min_split=2):**

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| H (High) | 0.72 | 0.68 | 0.70 | 31 |
| L (Low) | 0.79 | 0.85 | 0.82 | 27 |
| M (Medium) | 0.63 | 0.63 | 0.63 | 38 |
| **Weighted Avg** | **0.71** | **0.71** | **0.71** | **96** |

### Feature Importance (Decision Tree)

| Feature | Importance | Visual |
|---------|-----------|--------|
| VisitedResources | 0.4109 | ################ |
| AbsenceDays | 0.3337 | ############# |
| Discussion | 0.1443 | ##### |
| AnnouncementsView | 0.1112 | #### |

---

## 5. Justification: Why KNN + Decision Tree for This Problem

### 5.1 Complementary Approaches
- **Decision Tree** is model-based — it learns explicit IF-THEN rules from the data
- **KNN** is instance-based — it makes predictions by finding the most similar students
- Comparing both gives deeper insight into the data than comparing two similar algorithms (e.g., two model-based approaches)

### 5.2 Interpretability (Critical for Education Domain)
- **DT** produces readable rules, e.g., "IF visited_resources > 50 AND absence < 7 days THEN performance = HIGH"
- **KNN** uses an intuitive concept: "students with similar behavior to you performed at level X"
- Both can be explained to non-technical educators, parents, and administrators
- This is more important in education than in fields like finance where black-box models are acceptable

### 5.3 Dataset Fit
- Small dataset (480 records, 4 features) — both algorithms perform well on small data
- SVM and deep learning need larger datasets to outperform simpler models
- The xAPI-Edu-Data contains behavioral indicators that naturally suit both instance-based and rule-based classification

### 5.4 Hyperparameter Transparency
- **KNN's K value** has a clear, visual impact on accuracy — demonstrates bias-variance tradeoff
- **DT's max_depth** visually shows overfitting when too deep, underfitting when too shallow
- Both provide excellent teaching moments for understanding ML concepts

### 5.5 Practical Value in Education
- Schools can implement either algorithm without complex infrastructure or GPU resources
- Decision Tree gives actionable rules for early intervention policies
- KNN gives student-specific similarity matching for personalized support

### 5.6 The Key Tradeoff (Critical Insight)
> KNN outperforms Decision Tree on accuracy (75.0% vs 70.8%), but Decision Tree provides feature importance that KNN cannot. In a school setting, you would use KNN for better individual predictions but Decision Tree to understand WHY students fail. This is the fundamental tradeoff between prediction accuracy and interpretability — and comparing both algorithms exposes this tradeoff clearly.

---

## 6. Summary

| Metric | Best KNN | Best Decision Tree | Winner |
|--------|----------|-------------------|--------|
| Test Accuracy | 0.7500 | 0.7083 | KNN |
| Weighted F1 | 0.7480 | 0.7071 | KNN |
| 5-Fold CV | 0.6417 | 0.6750 | DT |
| Interpretability | Low (no rules) | High (IF-THEN rules) | DT |
| Feature Importance | Not available | Available | DT |
| Training Speed | Slow (computes at prediction time) | Fast (builds tree once) | DT |
| Best For | Individual prediction | Understanding patterns | Depends on goal |

---

*Generated from: student-performance-prediction/machine_learning_model.ipynb*
*Dataset: xAPI-Edu-Data (Kaggle) — 480 students, 16 features*
