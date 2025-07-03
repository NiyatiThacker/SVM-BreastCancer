# 🧠 Support Vector Machines (SVM) for Binary Classification

## 📌 Objective
To build and evaluate a **binary classification model** using **Support Vector Machines (SVM)** with both **linear** and **non-linear (RBF) kernels** on the **Breast Cancer Wisconsin Dataset**. The goal is to predict whether a tumor is **malignant (1)** or **benign (0)** based on medical features.

---

## 📁 Dataset Used
**breast-cancer.csv**  
- Samples: 569  
- Features: 30 numeric features (e.g., radius, texture, area, etc.)  
- Target: `diagnosis` column (B = Benign, M = Malignant)
- Source: Kaggle

---

## 🛠️ Tools & Libraries
- Python 🐍
- Pandas, NumPy
- Scikit-learn (SVC, GridSearchCV, metrics, preprocessing)
- Matplotlib, Seaborn (for visualizations)

---

## 📖 What is SVM?

Support Vector Machine (SVM) is a powerful supervised learning algorithm used for **classification** tasks. It works by:

- Drawing a boundary (called a **hyperplane**) that separates the classes with the **maximum margin**
- Using **support vectors** (the closest data points to the hyperplane) to define this boundary
- Applying **kernel tricks** to transform data into higher dimensions for non-linear classification

### 🔸 Linear Kernel:
Draws a **straight decision boundary**; ideal when data is linearly separable.

### 🔸 RBF Kernel:
Uses a **non-linear curved decision boundary** by mapping input features into higher-dimensional space. Great for capturing complex patterns.

---

## ✅ Steps Followed

### 1. Load & Explore Data
- Loaded `breast-cancer.csv` using Pandas
- Dropped the `id` column
- Converted `diagnosis` labels:
  - `'M'` → `1` (Malignant)
  - `'B'` → `0` (Benign)

### 2. Preprocess Data
- Separated features (`X`) and target (`y`)
- Performed an 80-20 train-test split
- Scaled features using `StandardScaler`  
  *(Important: SVM is distance-based and highly sensitive to feature scale)*

### 3. Linear SVM Model
- Trained using `SVC(kernel='linear')`
- Evaluated using confusion matrix, classification report, and accuracy score

> 📈 **Test Accuracy (Linear SVM):** `95.61%`  
> ✅ Performed well, but still had 3 false positives and 2 false negatives.

### 4. RBF Kernel SVM Model
- Trained using `SVC(kernel='rbf')` to allow non-linear classification
- Showed better accuracy and lower false positives

> 📈 **Test Accuracy (RBF Kernel):** `98.25%`  
> ✅Detected all benign cases correctly (no false positives)

### 5. Hyperparameter Tuning with GridSearchCV
Performed grid search on `C` and `gamma` to improve model generalization.

```python
param_grid = {
    'C': [0.1, 1, 10, 100],
    'gamma': [1, 0.1, 0.01, 0.001],
    'kernel': ['rbf']
}
```

- Used 5-fold cross-validation
- Refit best model on full training data

>  **Best Parameters:** `C = 100`, `gamma = 0.001`  
>  **Best Cross-Validation Accuracy:** `97.36%`  
>  **Final Test Accuracy (Tuned):** `98.25%`

---

##  Grid Search Heatmap

The heatmap below visualizes cross-validation accuracy for different `C` and `gamma` combinations:

![image](https://github.com/user-attachments/assets/7bcc12b2-c112-4532-a6a5-8aebd458ed80)


### 🔎 Insights:
- Best score at **`C = 100`, `gamma = 0.001`**
- **High `gamma` values (like 1.0)** lead to overfitting and poor generalization
- **Low `gamma` + high `C`** gave the best balance of accuracy and robustness

---

## 📊 Final Evaluation

| Metric        | Linear SVM | RBF SVM | Tuned RBF SVM |
|---------------|------------|---------|----------------|
| Accuracy      | 95.61%     | 98.25%  | 98.25% ✅      |
| Precision (1) | 0.93       | 1.00    | 1.00 ✅        |
| Recall (1)    | 0.95       | 0.95    | 0.95 ✅        |
| F1-Score (1)  | 0.94       | 0.98    | 0.98 ✅        |
| FP/FN         | 3/2        | 0/2     | 0/2 ✅         |

---

## 📌 Key Learnings

- **Feature Scaling is crucial** for distance-based models like SVM
- **Linear kernels** work well for simple, linearly separable data
- **RBF kernels** capture complex relationships and improve accuracy
- **Hyperparameter tuning (C, gamma)** can significantly improve model performance
- GridSearchCV helps **find the optimal balance between bias and variance**

---

## ✅ Conclusion

This project demonstrates the power and flexibility of SVMs in a real-world medical classification task. Through careful preprocessing, model selection, and hyperparameter tuning, we achieved a **very high accuracy of 98.25%**, with minimal false predictions.

SVMs, especially with RBF kernels, are a great choice for binary classification tasks with structured, scaled numerical data.

---

## ✍️ Author

**Niyati Thacker**  
3rd Year B.Tech Computer Science & Engineering Student  
Efficient in Python, Data Science, Machine Learning, Scikit-learn  
📧 niyatiswork1@gmail.com  
🔗 [GitHub Profile](https://github.com/NiyatiThacker)

---
