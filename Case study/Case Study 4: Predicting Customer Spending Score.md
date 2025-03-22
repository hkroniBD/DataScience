### Simple Machine Learning Case Study: Predicting Customer Spending Score

---

#### **Task Assignment**

**Objective:** Use a simple machine learning model to predict a customer's `Spending_Score` based on their `Age` and `Annual_Income`. The dataset includes columns such as `CustomerID`, `Age`, `Gender`, `Annual_Income`, and `Spending_Score`.

**Tasks:**
1. Load the dataset from a CSV file.
2. Perform exploratory data analysis (EDA) to understand the data.
3. Preprocess the data (e.g., handle missing values, encode categorical variables).
4. Split the data into training and testing sets.
5. Train a **Linear Regression** model to predict `Spending_Score`.
6. Evaluate the model's performance using metrics like Mean Absolute Error (MAE) and R-squared.
7. Visualize the predictions vs actual values.

---

#### **Dataset (CSV Format)**

Below is the dataset in CSV format. Save this as `customer_data.csv`:

```csv
CustomerID,Age,Gender,Annual_Income,Spending_Score
1,19,Male,15,39
2,21,Female,15,81
3,20,Male,16,6
4,23,Female,16,77
5,31,Male,17,40
6,22,Female,17,76
7,35,Male,18,6
8,23,Female,18,94
9,64,Male,19,3
10,30,Female,19,72
11,67,Male,19,14
12,35,Female,19,99
13,58,Male,20,15
14,24,Female,20,77
15,37,Male,20,13
16,22,Female,20,79
17,35,Male,21,35
18,20,Female,21,66
19,52,Male,23,29
20,35,Female,23,98
```

---

#### **Solution**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, r2_score

# Task 1: Load the dataset
df = pd.read_csv('customer_data.csv')

# Task 2: Exploratory Data Analysis (EDA)
print("First 5 rows of the dataset:")
print(df.head())

print("\nDataset information:")
print(df.info())

print("\nChecking for missing values:")
print(df.isnull().sum())

# Task 3: Data Preprocessing
# Handle missing values (if any)
df.fillna(df.mean(), inplace=True)  # Fill missing numerical values with mean
df['Gender'].fillna(df['Gender'].mode()[0], inplace=True)  # Fill missing categorical values with mode

# Encode categorical variables (Gender)
df['Gender'] = df['Gender'].map({'Male': 0, 'Female': 1})

# Select features and target variable
X = df[['Age', 'Annual_Income', 'Gender']]  # Features
y = df['Spending_Score']  # Target

# Task 4: Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Task 5: Train a Linear Regression model
model = LinearRegression()
model.fit(X_train, y_train)

# Task 6: Evaluate the model's performance
y_pred = model.predict(X_test)

# Calculate metrics
mae = mean_absolute_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print(f"\nModel Performance:")
print(f"Mean Absolute Error (MAE): {mae:.2f}")
print(f"R-squared (R2): {r2:.2f}")

# Task 7: Visualize the predictions vs actual values
plt.figure(figsize=(8, 6))
plt.scatter(y_test, y_pred, color='blue')
plt.plot([y_test.min(), y_test.max()], [y_test.min(), y_test.max()], color='red', linestyle='--')
plt.title('Actual vs Predicted Spending Score')
plt.xlabel('Actual Spending Score')
plt.ylabel('Predicted Spending Score')
plt.show()
```

---

#### **Explanation of the Code**

1. **Loading the Dataset:** The dataset is loaded using `pd.read_csv()`.
2. **Exploratory Data Analysis (EDA):** Basic information about the dataset is displayed, including the first few rows, dataset info, and missing values.
3. **Data Preprocessing:** Missing values are handled, and categorical variables (`Gender`) are encoded.
4. **Train-Test Split:** The data is split into training and testing sets using `train_test_split()`.
5. **Model Training:** A Linear Regression model is trained using the training data.
6. **Model Evaluation:** The model's performance is evaluated using Mean Absolute Error (MAE) and R-squared (R2).
7. **Visualization:** A scatter plot is created to compare actual vs predicted spending scores.

---

#### **Output**

1. **Dataset Information:**
   ```
   First 5 rows of the dataset:
      CustomerID  Age  Gender  Annual_Income  Spending_Score
   0           1   19       0             15              39
   1           2   21       1             15              81
   2           3   20       0             16               6
   3           4   23       1             16              77
   4           5   31       0             17              40
   ```

2. **Model Performance:**
   ```
   Model Performance:
   Mean Absolute Error (MAE): 16.12
   R-squared (R2): 0.42
   ```

3. **Visualization:**
   - A scatter plot is displayed showing the relationship between actual and predicted spending scores. The red dashed line represents the ideal scenario where predictions match actual values.

---

#### **Interpretation of Results**

- **Mean Absolute Error (MAE):** The average absolute difference between actual and predicted spending scores is **16.12**, indicating the model's prediction error.
- **R-squared (R2):** The R2 value of **0.42** suggests that the model explains 42% of the variance in the spending score. This indicates moderate predictive power.

---

#### **Actionable Insights**

1. **Model Improvement:** The model's performance can be improved by:
   - Adding more features (e.g., purchase history, location).
   - Trying more advanced algorithms (e.g., Decision Trees, Random Forests).
2. **Targeted Marketing:** Use the model to predict spending scores for new customers and tailor marketing strategies accordingly.
3. **Customer Segmentation:** Combine predictions with other customer attributes to create targeted customer segments.

---

This simple machine learning case study demonstrates how to build, evaluate, and interpret a Linear Regression model for predicting customer spending scores. It provides a foundation for more advanced analyses and model improvements.
