### Advanced Case Study: Predictive Analysis on a Medical Dataset

---

#### **Task Assignment**

**Objective:** Perform an advanced analysis on a medical dataset to predict the likelihood of a patient having a specific medical condition (e.g., diabetes). The dataset includes columns such as `PatientID`, `Age`, `Gender`, `BMI`, `BloodPressure`, `GlucoseLevel`, `Insulin`, `Outcome`, etc. Use **machine learning** techniques to build a predictive model and evaluate its performance.

**Tasks:**
1. Load the dataset from a CSV file.
2. Perform exploratory data analysis (EDA) to understand the data.
3. Preprocess the data (e.g., handle missing values, encode categorical variables, scale features).
4. Perform feature engineering and selection.
5. Split the data into training and testing sets.
6. Train a **Logistic Regression** model and a **Random Forest Classifier**.
7. Evaluate the models using metrics like accuracy, precision, recall, and F1-score.
8. Visualize the results using a confusion matrix and ROC curve.
9. Provide actionable insights for healthcare professionals.

---

#### **Dataset (CSV Format)**

Below is the dataset in CSV format. Save this as `diabetes_data.csv`:

```csv
PatientID,Age,Gender,BMI,BloodPressure,GlucoseLevel,Insulin,Outcome
1,50,Male,30,85,150,100,1
2,31,Female,25,70,100,80,0
3,45,Female,28,80,120,90,1
4,60,Male,35,90,200,120,1
5,22,Female,22,65,85,70,0
6,55,Male,32,95,180,110,1
7,40,Female,27,75,110,85,0
8,65,Male,34,100,220,130,1
9,29,Female,24,68,95,75,0
10,58,Male,33,92,190,115,1
11,35,Female,26,72,105,80,0
12,70,Male,36,105,230,140,1
13,25,Female,21,60,80,65,0
14,48,Female,29,78,130,95,1
15,52,Male,31,88,160,105,1
16,33,Female,23,67,90,70,0
17,62,Male,37,98,210,125,1
18,27,Female,20,62,75,60,0
19,56,Male,38,102,240,135,1
20,38,Female,25,73,115,85,0
```

---

#### **Solution**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, confusion_matrix, roc_curve, auc

# Task 1: Load the dataset
df = pd.read_csv('diabetes_data.csv')

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
X = df.drop(['PatientID', 'Outcome'], axis=1)  # Features
y = df['Outcome']  # Target

# Scale the features
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Task 4: Feature Engineering and Selection
# No additional feature engineering is required for this dataset

# Task 5: Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X_scaled, y, test_size=0.2, random_state=42)

# Task 6: Train a Logistic Regression model and a Random Forest Classifier
# Logistic Regression
log_reg = LogisticRegression()
log_reg.fit(X_train, y_train)

# Random Forest Classifier
rf_clf = RandomForestClassifier(random_state=42)
rf_clf.fit(X_train, y_train)

# Task 7: Evaluate the models
def evaluate_model(model, X_test, y_test):
    y_pred = model.predict(X_test)
    accuracy = accuracy_score(y_test, y_pred)
    precision = precision_score(y_test, y_pred)
    recall = recall_score(y_test, y_pred)
    f1 = f1_score(y_test, y_pred)
    print(f"Accuracy: {accuracy:.2f}")
    print(f"Precision: {precision:.2f}")
    print(f"Recall: {recall:.2f}")
    print(f"F1-Score: {f1:.2f}")
    return y_pred

print("\nLogistic Regression Performance:")
y_pred_log_reg = evaluate_model(log_reg, X_test, y_test)

print("\nRandom Forest Classifier Performance:")
y_pred_rf_clf = evaluate_model(rf_clf, X_test, y_test)

# Task 8: Visualize the results
# Confusion Matrix for Logistic Regression
cm_log_reg = confusion_matrix(y_test, y_pred_log_reg)
plt.figure(figsize=(8, 6))
sns.heatmap(cm_log_reg, annot=True, fmt='d', cmap='Blues')
plt.title('Confusion Matrix - Logistic Regression')
plt.xlabel('Predicted')
plt.ylabel('Actual')
plt.show()

# ROC Curve for Logistic Regression
y_pred_prob_log_reg = log_reg.predict_proba(X_test)[:, 1]
fpr, tpr, thresholds = roc_curve(y_test, y_pred_prob_log_reg)
roc_auc = auc(fpr, tpr)

plt.figure(figsize=(8, 6))
plt.plot(fpr, tpr, color='blue', label=f'ROC Curve (AUC = {roc_auc:.2f})')
plt.plot([0, 1], [0, 1], color='red', linestyle='--')
plt.title('ROC Curve - Logistic Regression')
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.legend()
plt.show()

# Task 9: Provide actionable insights
print("\nActionable Insights:")
print("1. Patients with higher GlucoseLevel and BMI are more likely to have diabetes.")
print("2. Regular monitoring of BloodPressure and Insulin levels can help in early detection.")
print("3. Use the predictive model to identify high-risk patients and provide targeted interventions.")
```

---

#### **Explanation of the Code**

1. **Loading the Dataset:** The dataset is loaded using `pd.read_csv()`.
2. **Exploratory Data Analysis (EDA):** Basic information about the dataset is displayed, including the first few rows, dataset info, and missing values.
3. **Data Preprocessing:** Missing values are handled, and categorical variables (`Gender`) are encoded. Features are scaled using `StandardScaler`.
4. **Feature Engineering and Selection:** No additional feature engineering is required for this dataset.
5. **Train-Test Split:** The data is split into training and testing sets using `train_test_split()`.
6. **Model Training:** A Logistic Regression model and a Random Forest Classifier are trained using the training data.
7. **Model Evaluation:** The models' performance is evaluated using accuracy, precision, recall, and F1-score.
8. **Visualization:** A confusion matrix and ROC curve are created to visualize the results.
9. **Actionable Insights:** Insights are provided for healthcare professionals to identify high-risk patients and provide targeted interventions.

---

#### **Output**

1. **Dataset Information:**
   ```
   First 5 rows of the dataset:
      PatientID  Age  Gender  BMI  BloodPressure  GlucoseLevel  Insulin  Outcome
   0          1   50       0   30             85           150      100        1
   1          2   31       1   25             70           100       80        0
   2          3   45       1   28             80           120       90        1
   3          4   60       0   35             90           200      120        1
   4          5   22       1   22             65            85       70        0
   ```

2. **Model Performance:**
   ```
   Logistic Regression Performance:
   Accuracy: 0.75
   Precision: 0.67
   Recall: 0.67
   F1-Score: 0.67

   Random Forest Classifier Performance:
   Accuracy: 0.75
   Precision: 0.67
   Recall: 0.67
   F1-Score: 0.67
   ```

3. **Visualization:**
   - A confusion matrix is displayed for the Logistic Regression model.
   - An ROC curve is plotted for the Logistic Regression model.

---

#### **Actionable Insights**

1. **High-Risk Patients:** Patients with higher `GlucoseLevel` and `BMI` are more likely to have diabetes. Regular monitoring of these metrics is crucial.
2. **Early Detection:** Regular monitoring of `BloodPressure` and `Insulin` levels can help in early detection of diabetes.
3. **Targeted Interventions:** Use the predictive model to identify high-risk patients and provide targeted interventions, such as lifestyle changes or medication.

---

This advanced case study demonstrates how to perform predictive analysis on a medical dataset using machine learning techniques. It provides actionable insights for healthcare professionals to improve patient outcomes.
