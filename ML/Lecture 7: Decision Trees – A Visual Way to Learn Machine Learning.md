## 🎓 **Lecture 7: Decision Trees – A Visual Way to Learn Machine Learning**

**Series:** Machine Learning for Non-IT Students
**Instructor:** HK Roni, EEE, HSTU

---

### 🗂️ **Lecture Outline**

1. What is a Decision Tree?
2. Real-Life Analogy
3. Components of a Decision Tree
4. Classification vs Regression Tree
5. Python Example: Pass/Fail Prediction
6. Visualizing the Tree
7. Summary and Homework

---

### 1️⃣ **What is a Decision Tree?**

A **Decision Tree** is a machine learning model that makes decisions by asking a series of **yes/no** or **true/false** questions.

> Think of it like a flowchart:
> If X is true → go left, else → go right.

It can be used for:

* **Classification** (e.g., pass or fail)
* **Regression** (e.g., predicting marks or salary)

---

### 2️⃣ **Real-Life Analogy**

> Imagine deciding whether to go outside:
>
> * Is it raining?
>      - Yes → Stay home
>      - No → Is it cold?
>          - Yes → Wear a jacket
>          - No → Go out in T-shirt

This is a simple **decision tree**.

---

### 3️⃣ **Components of a Decision Tree**

| Term          | Meaning                                     |
| ------------- | ------------------------------------------- |
| **Root Node** | The first question or condition             |
| **Branch**    | The outcome (yes/no) of a decision          |
| **Leaf Node** | Final decision or result                    |
| **Split**     | Process of dividing data based on condition |

---

### 4️⃣ **Classification vs Regression**

| Type           | Purpose               | Example Output    |
| -------------- | --------------------- | ----------------- |
| Classification | Categorize data       | Pass/Fail, Yes/No |
| Regression     | Predict numeric value | Marks, Salary     |

---

### 5️⃣ **Python Example: Predicting Pass/Fail Based on Study Hours**

#### Dataset:

| Hours\_Studied | Attended\_Class | Result |
| -------------- | --------------- | ------ |
| 2              | No              | Fail   |
| 4              | Yes             | Fail   |
| 6              | Yes             | Pass   |
| 8              | Yes             | Pass   |
| 1              | No              | Fail   |
| 9              | Yes             | Pass   |

---

#### 🧑‍💻 Step-by-Step Python Code:

```python
import pandas as pd
from sklearn.tree import DecisionTreeClassifier
from sklearn.preprocessing import LabelEncoder
from sklearn.tree import plot_tree
import matplotlib.pyplot as plt

# Step 1: Create dataset
data = {
    'Hours_Studied': [2, 4, 6, 8, 1, 9],
    'Attended_Class': ['No', 'Yes', 'Yes', 'Yes', 'No', 'Yes'],
    'Result': ['Fail', 'Fail', 'Pass', 'Pass', 'Fail', 'Pass']
}

df = pd.DataFrame(data)

# Step 2: Encode categorical values
le = LabelEncoder()
df['Attended_Class'] = le.fit_transform(df['Attended_Class'])  # No=0, Yes=1
df['Result'] = le.fit_transform(df['Result'])  # Fail=0, Pass=1

# Step 3: Train the decision tree
X = df[['Hours_Studied', 'Attended_Class']]
y = df['Result']

model = DecisionTreeClassifier()
model.fit(X, y)

# Step 4: Visualize the decision tree
plt.figure(figsize=(10,6))
plot_tree(model, feature_names=['Hours_Studied', 'Attended_Class'], class_names=['Fail', 'Pass'], filled=True)
plt.title("Decision Tree to Predict Pass/Fail")
plt.show()
```

---

### ✅ What You See

A colorful **tree diagram** that:

* Starts at "Hours\_Studied"
* Splits based on thresholds
* Ends in **leaf nodes** that say **Pass** or **Fail**

---

### 6️⃣ **Prediction**

You can now predict if a student will pass based on input:

```python
print(model.predict([[5, 1]]))  # 5 hours, attended → likely Pass
print(model.predict([[2, 0]]))  # 2 hours, not attended → likely Fail
```

---

### ✅ Summary of Lecture 7

* A **decision tree** breaks data into smaller decisions
* It is very **visual** and easy to understand
* Works for **classification** and **regression**
* You trained and visualized a tree using real data

---

### 🧠 Homework

1. Create your own dataset with:

   * "Study Time", "Sleep Hours", "Passed Exam"
2. Train a decision tree and visualize it.
3. Predict output for new entries.
4. Change the tree’s **max\_depth** to control size:

```python
DecisionTreeClassifier(max_depth=2)
```

---
