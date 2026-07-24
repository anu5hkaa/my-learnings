# 🏠 House Price Prediction using Multiple Linear Regression

## 📌 Project Overview

This project focuses on predicting residential house prices using the **Multiple Linear Regression** algorithm on the **Ames Housing Dataset**. The primary objective of this project was not only to build a predictive model but also to understand the complete machine learning workflow involved in solving a real-world regression problem.

Throughout this project, I learned how data preprocessing, feature engineering, multicollinearity analysis, and regression assumptions affect the overall performance of a regression model.

---

# 📂 Dataset Information

- **Dataset:** Ames Housing Dataset
- **Problem Type:** Regression
- **Target Variable:** `SalePrice`
- **Initial Features:** 82
- **Goal:** Predict the selling price of a house using different housing characteristics.

---

# 🎯 Objective

The goal of this project is to predict house prices accurately while understanding the mathematical concepts behind Multiple Linear Regression and implementing proper data preprocessing techniques before model training.

---

# 🧠 My Understanding

Working on this project helped me understand that Machine Learning is not just about applying an algorithm. The quality of the data directly impacts the quality of predictions.

I learned how **Multiple Linear Regression** works mathematically. The model attempts to find the **best-fit line** that minimizes the difference between actual and predicted values.

Initially, the model starts with random coefficients. Using the **Mean Squared Error (MSE)** cost function, it measures the prediction error. The coefficients are continuously updated using **Gradient Descent**, which moves towards the minimum point of the cost function. Once the cost function converges, the optimized coefficients become the parameters of the final regression equation.

During this project, I also understood why proper preprocessing is essential before training a regression model.

Instead of treating every missing value as missing data, I learned that many missing values actually represented the absence of certain facilities such as garages, basements, fireplaces, and masonry veneer. Therefore, these values were imputed appropriately rather than deleting valuable observations.

I also learned how to identify duplicate records, detect outliers using scatter plots, and remove only influential outliers while preserving valid luxury houses.

Another major concept I understood was **Multicollinearity**. Using the **Variance Inflation Factor (VIF)**, I identified highly correlated independent variables and removed mathematically dependent features to improve model stability.

Finally, I evaluated the model using different regression evaluation metrics and verified the assumptions of Multiple Linear Regression using Residual Plots and Q-Q Plots.

This project significantly improved my understanding of both the theoretical concepts and practical implementation of Multiple Linear Regression.

---

# ⚙️ Project Workflow

```text
Load Dataset
        │
        ▼
Data Exploration
        │
        ▼
Missing Value Analysis
        │
        ▼
Duplicate Value Check
        │
        ▼
Dropping Unnecessary Features
        │
        ▼
Outlier Detection using Scatter Plots
        │
        ▼
Categorical Encoding (One-Hot Encoding)
        │
        ▼
Train-Test Split
        │
        ▼
Multicollinearity Analysis (VIF)
        │
        ▼
Multiple Linear Regression Model
        │
        ▼
Prediction
        │
        ▼
Model Evaluation
        │
        ▼
Regression Assumption Checking
```

---

# 🧹 Data Preprocessing

## Missing Value Treatment

The dataset contained multiple missing values.

Instead of removing rows directly, missing values were handled according to the meaning of each feature.

Examples include:

- Garage Features
- Basement Features
- Fireplace Quality
- Masonry Veneer
- Lot Frontage

For many categorical variables, missing values actually indicated the absence of a facility rather than missing information.

---

## Duplicate Values

The dataset was checked for duplicate observations before model training.

---

## Feature Removal

Non-informative identifier columns were removed from the dataset.

Examples:

- Order
- PID

---

## Outlier Detection

Outliers were detected using scatter plots between important numerical features and the target variable.

Features analyzed included:

- Gr Liv Area
- Lot Area
- Garage Area
- Total Basement Area

Only influential outliers were removed while preserving genuine high-priced properties.

---

## Encoding

Categorical variables were converted into numerical format using **One-Hot Encoding** (`drop_first=True`).

While implementing the project, I also understood that some categorical variables were ordinal in nature and could alternatively be encoded using ordinal encoding to preserve their natural ordering.

---

## Multicollinearity Analysis

Multicollinearity was evaluated using the **Variance Inflation Factor (VIF)**.

Perfectly dependent features were removed before model training to improve the stability of the regression coefficients.

---

# 📈 Multiple Linear Regression Assumptions

The following assumptions were studied and verified:

- ✅ Linearity
- ✅ Independence of observations
- ✅ Multicollinearity (using VIF)
- ✅ Normality of Residuals (Q-Q Plot)
- ✅ Homoscedasticity (Residual Plot)

---

# 📊 Model Performance

| Metric | Value |
|----------|------------|
| Mean Absolute Error (MAE) | **15,446.92** |
| Mean Squared Error (MSE) | **556,233,564.26** |
| Root Mean Squared Error (RMSE) | **23,584.60** |
| R² Score | **0.9310 (93.10%)** |

---

# 📚 Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Statsmodels
- SciPy

---

# 💡 Key Learnings

- Developed a complete understanding of the Multiple Linear Regression workflow.
- Learned how Gradient Descent optimizes model parameters by minimizing the cost function.
- Understood the importance of proper missing value treatment.
- Performed outlier detection using scatter plots.
- Applied One-Hot Encoding for categorical variables.
- Learned how to detect and reduce multicollinearity using VIF.
- Evaluated model performance using MAE, MSE, RMSE, and R² Score.
- Verified regression assumptions using Residual and Q-Q plots.
- Achieved an **R² Score of approximately 93%**, indicating that the model explains most of the variation in house prices.

---

# 🚀 Future Improvements

- Apply Ordinal Encoding for ordered categorical features.
- Compare Multiple Linear Regression with Ridge and Lasso Regression.
- Perform Hyperparameter Optimization.
- Explore Ensemble Regression models such as Random Forest Regressor and XGBoost Regressor.
- Build a deployment-ready web application using Streamlit or Flask.

---

# 📌 Conclusion

This project provided hands-on experience with the complete machine learning pipeline for a regression problem. From handling missing values and outliers to reducing multicollinearity and validating regression assumptions, every stage helped strengthen my understanding of practical machine learning.

Beyond building a predictive model, this project improved my understanding of data preprocessing, statistical assumptions, feature engineering, and model evaluation, making it an excellent learning experience in applying Multiple Linear Regression to real-world housing price prediction.
