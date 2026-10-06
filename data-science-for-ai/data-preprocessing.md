# Data Preprocessing & Feature Engineering

Data preprocessing is the foundational step in machine learning, transforming raw data into a clean, model-ready format.

## 1. Handling Missing Data

| Strategy | Description | Best For |
|---|---|---|
| **Deletion** | Dropping rows/columns with missing values. | Large datasets where missing data is random (< 5%). |
| **Mean/Median Imputation** | Replacing missing continuous values with the feature's mean or median. | Numerical features. Use median if outliers are present. |
| **Mode Imputation** | Replacing missing values with the most frequent category. | Categorical features. |
| **Predictive Imputation** | Using algorithms (like KNN) to predict the missing value. | Complex datasets where relationships exist between features. |

## 2. Feature Scaling

Distance-based algorithms (SVM, KNN, K-Means) and gradient descent require features to be on a similar scale.

*   **Standardization (Z-score Normalization):** Centers data around a mean of 0 with a standard deviation of 1.
    $$z = \frac{x - \mu}{\sigma}$$
*   **Min-Max Normalization:** Scales data to a fixed range, typically [0, 1].
    $$x_{norm} = \frac{x - x_{min}}{x_{max} - x_{min}}$$

## 3. Categorical Encoding

Models require numerical inputs. Categorical variables must be converted.

*   **Label Encoding:** Assigns a unique integer to each category (e.g., Red=1, Green=2). *Warning: Can introduce unintended ordinal relationships.*
*   **One-Hot Encoding:** Creates binary columns for each category. Best for nominal data. Can lead to the "curse of dimensionality" if cardinality is high.
*   **Target Encoding:** Replaces a category with the mean of the target variable for that category. Good for high-cardinality features.

## 4. Outlier Detection

*   **Z-Score:** Identifies points further than $3\sigma$ from the mean.
*   **Interquartile Range (IQR):** Identifies points outside $1.5 \times IQR$ below $Q1$ or above $Q3$.
    $$IQR = Q3 - Q1$$
    $$Lower Bound = Q1 - 1.5 \times IQR$$
    $$Upper Bound = Q3 + 1.5 \times IQR$$
    

*©️ Created by Wecncode Developer Community!*
