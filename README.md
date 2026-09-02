# Cross-Validation Techniques: K-Fold Cross-Validation and Model Performance Evaluation

## 📌 Project Overview

This project demonstrates the implementation of **K-Fold Cross-Validation** for evaluating the performance and consistency of a machine learning regression model.

A **Sales dataset** is used to predict `Profit` based on important sales-related features. A **Random Forest Regression** model is trained, and **5-Fold Cross-Validation** is applied to evaluate its performance across multiple subsets of the training data.

The project also evaluates the final model using **R² Score, Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE)**.

---

## 🎯 Objectives

* Understand the concept of Cross-Validation.
* Implement **K-Fold Cross-Validation**.
* Train a Random Forest Regression model.
* Evaluate model performance across multiple folds.
* Calculate Mean Cross-Validation R² Score.
* Analyze the consistency of model performance.
* Evaluate the model on unseen test data.
* Analyze prediction errors.
* Identify important features for Profit prediction.
* Save the trained machine learning model.
* Export the evaluation results.

---

## 📊 Dataset

The project uses the **Sales_Data** sheet from the Sales Excel dataset.

### Selected Features

The following numerical features are used:

* `Quantity`
* `Unit_Price`
* `Discount`
* `Sales`
* `Profit_Margin`

### Target Variable

```text
Profit
```

The objective is to predict the `Profit` generated from a sales transaction.

---

## 🧠 Machine Learning Model

### Random Forest Regression

A **Random Forest Regressor** is used for predicting Profit.

Random Forest is an ensemble learning algorithm that combines multiple decision trees to produce a more robust prediction.

Configuration used:

```text
n_estimators = 100
random_state = 42
```

---

## 🔄 K-Fold Cross-Validation

The project uses **5-Fold Cross-Validation**.

The training dataset is divided into five subsets:

```text
Fold 1 → Validation | Folds 2–5 → Training
Fold 2 → Validation | Folds 1,3–5 → Training
Fold 3 → Validation | Folds 1,2,4,5 → Training
Fold 4 → Validation | Folds 1–3,5 → Training
Fold 5 → Validation | Folds 1–4 → Training
```

The model is trained and validated five times.

The individual R² scores are then used to calculate:

* Mean Cross-Validation R²
* Standard Deviation

A higher mean R² indicates better predictive performance, while a lower standard deviation indicates more consistent performance across folds.

---

## 🔬 Project Workflow

```text
Sales Excel Dataset
        ↓
Load Sales_Data Sheet
        ↓
Data Inspection
        ↓
Handle Missing Values
        ↓
Feature Selection
        ↓
Target Selection (Profit)
        ↓
Train-Test Split
        ↓
Feature Standardization
        ↓
Random Forest Regression
        ↓
5-Fold Cross-Validation
        ↓
Model Evaluation
        ↓
Error Analysis
        ↓
Feature Importance
        ↓
Visualizations
        ↓
Save Model & Results
```

---

## 🛠️ Technologies Used

* Python
* Google Colab
* Pandas
* NumPy
* Matplotlib
* Scikit-learn
* Joblib
* Excel

---

## 📦 Python Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.model_selection import KFold, cross_val_score

from sklearn.preprocessing import StandardScaler

from sklearn.ensemble import RandomForestRegressor

from sklearn.metrics import (
    mean_absolute_error,
    mean_squared_error,
    r2_score
)

import joblib
```

---

## 📈 Evaluation Metrics

### 1. R² Score

R² measures how well the model explains the variation in the target variable.

A value closer to **1** indicates stronger predictive performance.

### 2. Mean Absolute Error (MAE)

MAE measures the average absolute difference between actual and predicted Profit.

Lower MAE indicates better performance.

### 3. Root Mean Squared Error (RMSE)

RMSE measures the square root of the average squared prediction error.

It gives greater importance to larger errors.

Lower RMSE indicates better performance.

### 4. Cross-Validation Standard Deviation

The standard deviation of the fold scores indicates how much the model's performance changes between different folds.

A smaller value indicates more stable performance.

---

## 📊 Visualizations

The project includes the following visualizations:

### 1. K-Fold Cross-Validation Performance

Shows the R² score obtained from each of the five folds.

### 2. Actual vs Predicted Profit

Compares the actual Profit values with the Profit values predicted by the Random Forest model.

### 3. Residual Analysis

Shows the difference between actual and predicted Profit.

### 4. Feature Importance

Displays the relative importance of:

```text
Quantity
Unit_Price
Discount
Sales
Profit_Margin
```

for predicting Profit.

---

## 📁 Project Structure

```text
cross-validation-sales-performance/
│
├── Cross_Validation_Sales_Results.xlsx
├── sales_profit_random_forest_model.pkl
├── sales_profit_scaler.pkl
├── Cross_Validation_Sales.ipynb
└── README.md
```

---

## 💾 Saved Model Files

### Random Forest Model

```text
sales_profit_random_forest_model.pkl
```

Contains the trained Random Forest Regression model.

### Feature Scaler

```text
sales_profit_scaler.pkl
```

Contains the fitted `StandardScaler` used during preprocessing.

### Results File

```text
Cross_Validation_Sales_Results.xlsx
```

Contains the K-Fold Cross-Validation scores and final test performance metrics.

---

## 🔮 Profit Prediction

A reusable prediction function was created to predict Profit for new sales data.

Example input:

```python
predicted_profit = predict_profit(
    quantity=5,
    unit_price=1000,
    discount=0.10,
    sales=4500,
    profit_margin=0.20
)

print(f"Predicted Profit: {predicted_profit:.2f}")
```

The trained model processes the new input and returns the predicted Profit.

---

## 📋 Results

The project evaluates the model using:

```text
Fold 1 R²
Fold 2 R²
Fold 3 R²
Fold 4 R²
Fold 5 R²

Mean CV R²
CV Standard Deviation

Test R²
Test MAE
Test RMSE
```

The exact values are generated from the Sales dataset during execution and are available in:

```text
Cross_Validation_Sales_Results.xlsx
```

---

## 🚀 How to Run the Project

### Step 1: Open Google Colab

Open a new Google Colab notebook.

### Step 2: Upload the Dataset

Upload the Sales Excel dataset containing the:

```text
Sales_Data
```

sheet.

### Step 3: Run the Notebook

Execute the notebook cells sequentially.

The notebook performs:

```text
Data Loading
      ↓
Preprocessing
      ↓
Model Training
      ↓
K-Fold Cross-Validation
      ↓
Evaluation
      ↓
Visualization
      ↓
Model Saving
```

### Step 4: Download Results

After execution, download:

```text
Cross_Validation_Sales_Results.xlsx
sales_profit_random_forest_model.pkl
sales_profit_scaler.pkl
```

---

## 🔍 Key Findings

The project demonstrates that K-Fold Cross-Validation provides a more reliable assessment of model performance than relying on a single train-test split.

By evaluating the model across five different folds, it is possible to determine:

* Average predictive performance
* Performance variation
* Model stability
* Generalization capability

The final test-set evaluation provides an additional assessment of how well the trained model performs on unseen data.

---

## ⚠️ Limitations

* The project uses a limited set of numerical features.
* The model predicts Profit based only on the selected features.
* Categorical variables such as `Region`, `Category`, and `Customer_Segment` are not included in the current model.
* Cross-validation results depend on the dataset and selected features.
* Random Forest performance can change with different hyperparameters.

---

## 🔮 Future Improvements

Possible improvements include:

* Hyperparameter tuning using GridSearchCV or RandomizedSearchCV.
* Comparing Random Forest with Linear Regression, Gradient Boosting, and XGBoost.
* Including categorical variables using encoding techniques.
* Performing feature engineering.
* Testing different numbers of K-Folds.
* Creating a Streamlit prediction application.
* Deploying the trained model as a web service.
* Adding automated model evaluation.

---

## 🎓 Learning Outcomes

Through this project, the following concepts were implemented:

* Machine Learning Regression
* Train-Test Splitting
* Feature Scaling
* Random Forest Regression
* K-Fold Cross-Validation
* Model Performance Evaluation
* R² Score
* MAE
* RMSE
* Residual Analysis
* Feature Importance
* Model Serialization
* Prediction on New Data

---

## 👩‍💻 Author

**Sana Kishore**

Third-Year Computer Science / Data Analytics Student

---

## 📜 License

This project is intended for educational and academic purposes.
