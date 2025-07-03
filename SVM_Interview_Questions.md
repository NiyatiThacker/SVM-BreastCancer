
# 📋 SVM Interview Questions



### 1.  What is a support vector?
A **support vector** is a data point that lies closest to the decision boundary (or hyperplane). These are the critical elements of the dataset — removing them would change the position of the hyperplane. SVM uses these support vectors to define the margin and create the optimal separator between classes.

---

### 2.  What does the `C` parameter do?
The `C` parameter in SVM controls the **trade-off between achieving a low error on the training data and maintaining a smooth decision boundary**.
- **Low C**: Encourages a wider margin (soft margin), allowing some misclassifications.
- **High C**: Tries to classify all training examples correctly (hard margin), which may lead to overfitting.

---

### 3.  What are kernels in SVM?
**Kernels** are functions that transform the original feature space into a higher-dimensional space to make data **linearly separable**. Common kernels:
- **Linear**: No transformation; best for linearly separable data.
- **Polynomial**: Maps data to a polynomial space.
- **RBF (Radial Basis Function)**: Maps data using Gaussian functions; great for complex boundaries.

---

### 4.  What is the difference between linear and RBF kernel?
| Feature       | Linear Kernel                   | RBF Kernel                         |
|---------------|----------------------------------|------------------------------------|
| Use Case      | Linearly separable data          | Non-linearly separable data        |
| Decision Boundary | Straight line/hyperplane        | Curved/complex boundary            |
| Computation   | Faster, less complex             | More computationally intensive     |
| Flexibility   | Less flexible                    | More flexible                      |

---

### 5.  What are the advantages of SVM?
- Works well in high-dimensional spaces
- Effective when number of features > samples
- Robust to overfitting with proper regularization (C, kernel)
- Only depends on support vectors → efficient model

---

### 6.  Can SVMs be used for regression?
Yes! The regression counterpart of SVM is called **Support Vector Regression (SVR)**. It tries to fit the best function within a margin of tolerance (epsilon) around the actual values.

---

### 7.  What happens when data is not linearly separable?
SVM uses the **kernel trick** (e.g., RBF kernel) to **project the data into a higher-dimensional space** where a linear separator can exist. It also uses **soft margin** (with parameter C) to allow for some misclassifications.

---

### 8.  How is overfitting handled in SVM?
Overfitting is controlled through:
- **C**: Lower values allow for a softer margin (less overfitting)
- **gamma** (in RBF kernel): Lower values smooth the decision boundary
- **Kernel choice**: Using appropriate kernels avoids over-complexity

---
