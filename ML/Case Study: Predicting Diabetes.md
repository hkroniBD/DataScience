## 🩺 **Case Study: Predicting Diabetes from Health Data**

**Title:** Can We Predict if a Person Has Diabetes Using Health Measurements?
**Target Audience:** Non-IT Students (Beginner Level)
**Instructor:** HK Roni, EEE, HSTU

---

### 🎯 **Objective**

To use machine learning to predict the likelihood of **diabetes** based on common health metrics, empowering preventive health awareness.

---

### 🧩 **Dataset Overview**

This case study uses a simplified version of the **Pima Indians Diabetes Dataset**. Each row represents a patient with the following health indicators:

| Feature          | Description                      |
| ---------------- | -------------------------------- |
| Pregnancies      | Number of times pregnant         |
| Glucose          | Blood sugar level                |
| BloodPressure    | Diastolic blood pressure (mm Hg) |
| BMI              | Body Mass Index                  |
| Age              | Age of the patient               |
| Outcome (Target) | 1 = Diabetic, 0 = Non-diabetic   |

---

### 🧪 **Step-by-Step Implementation**

#### ✅ Step 1: Import Libraries and Load Data

```python
import pandas as pd

# Sample data (a few rows)
data = {
    'Pregnancies': [2, 4, 0, 1, 3],
    'Glucose': [120, 150, 85, 170, 95],
    'BloodPressure': [70, 80, 65, 90, 72],
    'BMI': [25.1, 30.5, 28.3, 35.6, 24.8],
    'Age': [22, 35, 19, 45, 29],
    'Outcome': [0, 1, 0, 1, 0]
}

df = pd.DataFrame(data)
```

---

#### ✅ Step 2: Define Features and Target

```python
X = df[['Pregnancies', 'Glucose', 'BloodPressure', 'BMI', 'Age']]
y = df['Outcome']
```

---

#### ✅ Step 3: Split Data into Train and Test Sets

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)
```

---

#### ✅ Step 4: Train a Logistic Regression Model

```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()
model.fit(X_train, y_train)
```

---

#### ✅ Step 5: Make Predictions and Evaluate

```python
y_pred = model.predict(X_test)

from sklearn.metrics import accuracy_score, confusion_matrix

print("Accuracy:", accuracy_score(y_test, y_pred))
print("Confusion Matrix:\n", confusion_matrix(y_test, y_pred))
```

---

#### ✅ Step 6: Predict on New Patient Data

```python
new_patient = [[3, 140, 75, 29.0, 34]]  # Format: [Preg, Glucose, BP, BMI, Age]
prediction = model.predict(new_patient)

if prediction[0] == 1:
    print("The patient is likely diabetic.")
else:
    print("The patient is not likely diabetic.")
```

---

### 📈 **Understanding the Results**

* **Higher glucose and BMI** often lead to a higher chance of diabetes.
* The model is able to provide **early risk predictions**.
* Logistic regression is good for **binary classification problems** like this.

---

### 📊 Optional: Feature Importance (Visual)

```python
import matplotlib.pyplot as plt

coefficients = model.coef_[0]
features = X.columns

plt.barh(features, coefficients)
plt.xlabel("Importance")
plt.title("Feature Impact on Diabetes Prediction")
plt.show()
```

---

### ✅ **Conclusion**

* Simple ML models can help predict critical health outcomes.
* Logistic Regression works well for Yes/No type predictions.
* Health care institutions can use such tools to guide patients early.

---

### 📘 Discussion Points

* Why might a prediction be wrong?
* Could we add more features (like insulin levels, cholesterol)?
* How could this be deployed in hospitals?

---

### 🧠 Homework for Students

1. Add another patient and predict their diabetes status.
2. Try using a **Decision Tree** instead of Logistic Regression.
3. Test with extreme values and discuss the results.

---
