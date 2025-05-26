## 📊 **Case Study: Predicting Student Performance Using Machine Learning**

**Title:** How Can We Predict a Student’s Final Grade Based on Study Habits and Attendance?
**Target Audience:** Non-IT Students (Beginner Level)
**Instructor:** HK Roni, EEE, HSTU

---

### 🎯 **Objective**

To use machine learning to **analyze student data** and **predict final exam performance**, helping teachers and institutions identify at-risk students early.

---

### 🧩 **Dataset Description**

Suppose we have a dataset with the following features for each student:

| Feature               | Description                          |
| --------------------- | ------------------------------------ |
| Hours\_Studied        | Number of hours student studied/week |
| Attendance\_Percent   | Class attendance in percentage       |
| Assignment\_Completed | Yes/No                               |
| Sleep\_Hours          | Daily sleep in hours                 |
| Final\_Result         | Pass/Fail (Target)                   |

#### Sample Data:

```python
data = {
    'Hours_Studied': [1, 5, 8, 2, 7, 3, 10, 4],
    'Attendance_Percent': [45, 80, 90, 60, 95, 50, 100, 70],
    'Assignment_Completed': ['No', 'Yes', 'Yes', 'No', 'Yes', 'No', 'Yes', 'Yes'],
    'Sleep_Hours': [4, 6, 7, 5, 8, 5, 7, 6],
    'Final_Result': ['Fail', 'Pass', 'Pass', 'Fail', 'Pass', 'Fail', 'Pass', 'Pass']
}
```

---

### 🧪 **Step-by-Step Data Analysis and Modeling**

#### ✅ Step 1: Import Libraries and Load Data

```python
import pandas as pd

df = pd.DataFrame(data)
print(df.head())
```

#### ✅ Step 2: Data Preprocessing

* Convert **Assignment\_Completed** and **Final\_Result** to numerical values

```python
from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()
df['Assignment_Completed'] = le.fit_transform(df['Assignment_Completed'])  # No=0, Yes=1
df['Final_Result'] = le.fit_transform(df['Final_Result'])  # Fail=0, Pass=1
```

#### ✅ Step 3: Define Features and Target

```python
X = df[['Hours_Studied', 'Attendance_Percent', 'Assignment_Completed', 'Sleep_Hours']]
y = df['Final_Result']
```

#### ✅ Step 4: Train-Test Split

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25, random_state=42)
```

#### ✅ Step 5: Train a Decision Tree Classifier

```python
from sklearn.tree import DecisionTreeClassifier

model = DecisionTreeClassifier()
model.fit(X_train, y_train)
```

#### ✅ Step 6: Make Predictions and Evaluate

```python
y_pred = model.predict(X_test)

from sklearn.metrics import accuracy_score, confusion_matrix

print("Accuracy:", accuracy_score(y_test, y_pred))
print("Confusion Matrix:\n", confusion_matrix(y_test, y_pred))
```

---

### 📉 **Visualization: Decision Tree**

```python
from sklearn.tree import plot_tree
import matplotlib.pyplot as plt

plt.figure(figsize=(12,6))
plot_tree(model, feature_names=X.columns, class_names=['Fail', 'Pass'], filled=True)
plt.title("Student Performance Prediction Tree")
plt.show()
```

---

### 🧠 **Insights from Analysis**

1. **Hours Studied** and **Attendance** are the most important predictors.
2. Students who completed assignments and studied more than 5 hours/week mostly passed.
3. Low attendance and <3 hours of study = high risk of failure.

---

### 📈 **Model Accuracy**

If accuracy is 87.5%, this means:

* The model correctly predicted 7 out of 8 student results.

---

### ✅ **Conclusions**

* Machine learning helps in **early warning systems** for student support.
* Teachers can intervene based on **predicted risk levels**.
* Models like **Decision Trees** are easy to interpret and apply.

---

### 🧠 **Homework for Students**

1. Add a new feature: `Internet_Usage_Hours`.
2. Retrain the model and see how accuracy changes.
3. Try using a **Logistic Regression** or **Random Forest** classifier.

---

