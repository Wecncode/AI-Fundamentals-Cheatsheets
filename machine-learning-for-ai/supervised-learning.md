# Supervised Learning Algorithms & Metrics

Supervised learning algorithms map input variables ($X$) to an output variable ($Y$) using labeled training data.

## 1. Core Algorithms

| Algorithm | Type | Core Concept | Key Hyperparameters |
|---|---|---|---|
| **Linear Regression** | Regression | Fits a line that minimizes the sum of squared residuals. | Learning rate, Regularization (L1/L2) |
| **Logistic Regression** | Classification | Uses a sigmoid function to output probabilities for binary classification. | Regularization strength ($C$), Penalty |
| **Decision Trees** | Both | Splits data into branches based on feature conditions to maximize Information Gain or minimize Gini Impurity. | Max depth, Min samples split |
| **Random Forest** | Both | Ensemble method that builds multiple decision trees and merges their predictions (Bagging). | Number of estimators, Max depth |
| **SVM** | Both | Finds the optimal hyperplane maximizing the margin between classes. | Kernel type, $C$ (Regularization), Gamma |
| **XGBoost** | Both | Sequential ensemble building trees that correct the errors of previous ones (Gradient Boosting). | Learning rate, Max depth, Subsample |

## 2. Mathematical Formulations

*   **Linear Regression Hypothesis:** $h_\theta(x) = \theta_0 + \theta_1x_1 + ... + \theta_nx_n = \theta^T x$
*   **Logistic Regression Hypothesis:** $h_\theta(x) = \frac{1}{1 + e^{-\theta^T x}}$
*   **Mean Squared Error (MSE):** $J(\theta) = \frac{1}{m} \sum_{i=1}^{m} (h_\theta(x^{(i)}) - y^{(i)})^2$
*   **Cross-Entropy Loss (Log Loss):** $J(\theta) = - \frac{1}{m} \sum_{i=1}^{m} [y^{(i)} \log(h_\theta(x^{(i)})) + (1 - y^{(i)}) \log(1 - h_\theta(x^{(i)}))]$

## 3. Evaluation Metrics (Classification)

*   **Precision:** Out of all positive predictions, how many were actually positive? $\frac{TP}{TP + FP}$
*   **Recall (Sensitivity):** Out of all actual positives, how many were predicted correctly? $\frac{TP}{TP + FN}$
*   **F1-Score:** Harmonic mean of Precision and Recall. $2 \times \frac{Precision \times Recall}{Precision + Recall}$
*   **ROC-AUC:** Measures the model's ability to distinguish between classes across all classification thresholds.


*   *©️ Created by Wecncode Developer Community!* 
