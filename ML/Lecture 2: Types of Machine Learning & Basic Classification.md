## 🎓 **Lecture 2: Types of Machine Learning & Basic Classification**


**Instructor:** HK Roni, EEE, HSTU

---

### 🗂️ **Lecture Outline**

1. Types of Machine Learning
2. Supervised vs Unsupervised Learning
3. Introduction to Classification
4. Simple KNN Classification Example
5. Summary and Homework

---

### 1️⃣ **Types of Machine Learning**

Machine learning can be grouped into three main types:

| Type                       | Description                                                           | Example                                         |
| -------------------------- | --------------------------------------------------------------------- | ----------------------------------------------- |
| **Supervised Learning**    | Learning with **labeled data** (inputs and correct outputs are given) | Predicting grades, classifying emails           |
| **Unsupervised Learning**  | Learning with **unlabeled data** (only inputs, no correct answers)    | Grouping similar customers, market segmentation |
| **Reinforcement Learning** | Learning by **trial and error**, like a game                          | Self-driving cars, game AI                      |

---

### 2️⃣ **Supervised vs Unsupervised: Simple Analogy**

|                            | Supervised                                              | Unsupervised                                                |
| -------------------------- | ------------------------------------------------------- | ----------------------------------------------------------- |
| 👩‍🏫 **Teacher present?** | Yes (provides correct answers)                          | No (learns patterns on its own)                             |
| 📘 **Example**             | You learn math by solving problems and checking answers | You group your books by size without knowing their subjects |

---

### 3️⃣ **Introduction to Classification**

**Classification** is a type of **supervised learning** where the output is a **category or class**, not a number.

> Example:
>
> * Spam or Not Spam
> * Pass or Fail
> * Disease or No Disease

---

### 4️⃣ **Simple Classification Example Using KNN**

#### 🧪 Problem:

We want to predict whether a student will **Pass or Fail** based on:

* Attendance
* Assignment Score

We will use **K-Nearest Neighbors (KNN)** algorithm.

#### ✅ Step-by-step Python Code

**Step 1: Import Required Libraries**

```python
import pandas as pd
from sklearn.neighbors import KNeighborsClassifier
```

**Step 2: Create Sample Dataset**

```python
data = {
    'Attendance': [90, 85, 60, 45, 95, 50],
    'Assignment': [88, 82, 60, 55, 90, 58],
    'Result': ['Pass', 'Pass', 'Pass', 'Fail', 'Pass', 'Fail']
}

df = pd.DataFrame(data)
```

**Step 3: Prepare Features and Labels**

```python
X = df[['Attendance', 'Assignment']]   # Features (inputs)
y = df['Result']                       # Labels (outputs)
```

**Step 4: Train the KNN Model**

```python
model = KNeighborsClassifier(n_neighbors=3)  # Use 3 nearest neighbors
model.fit(X, y)
```

**Step 5: Predict New Result**

```python
new_student = [[70, 65]]  # A new student’s data
prediction = model.predict(new_student)
print("Predicted Result:", prediction[0])
```

#### 📌 Expected Output:

```
Predicted Result: Pass
```

---

### 🔍 **How KNN Works (Simple Explanation)**

1. Looks at the 3 closest students (neighbors) to the new one.
2. Checks how many of them passed vs. failed.
3. Chooses the majority class as prediction.

---

### ✅ **Summary of Lecture 2**

* Machine Learning has three types: Supervised, Unsupervised, Reinforcement
* Classification is a supervised learning task that predicts **categories**
* You built a simple classification model using the **KNN algorithm**

---
