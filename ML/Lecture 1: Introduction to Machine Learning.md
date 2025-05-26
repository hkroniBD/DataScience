## 🎓 **Lecture 1: Introduction to Machine Learning**

**Series:** Machine Learning for Non-IT Students
**Instructor:** HK Roni, EEE, HSTU

---

### 🗂️ **Lecture Outline**

1. What is Machine Learning?
2. Why Do We Need Machine Learning?
3. Real-Life Applications of ML
4. Key Concepts in ML
5. Case Study: Predicting Student Grades (with Python)
6. Summary and Homework

---

### 1️⃣ **What is Machine Learning?**

**Machine Learning** is a method where computers learn from data to make decisions or predictions **without being directly programmed** for each specific task.

> **Analogy:** Just like a baby learns to walk by trying, falling, and improving—machines learn by analyzing data again and again.

---

### 2️⃣ **Why Do We Need Machine Learning?**

Traditional programming:

* We write **rules** → Computer follows them

Machine Learning:

* We give **data and examples** → Computer learns the rules itself

> **Example:** Instead of teaching a computer what a cat looks like, we show it 1000 cat pictures. It learns the pattern.

---

### 3️⃣ **Where is ML Used in Daily Life?**

| Area          | Example                          |
| ------------- | -------------------------------- |
| **Email**     | Spam detection                   |
| **Shopping**  | Product recommendations          |
| **Health**    | Predicting diseases              |
| **Finance**   | Credit score prediction          |
| **Transport** | Self-driving car decision making |

---

### 4️⃣ **Basic Terms (Explained Simply)**

| Term           | Meaning                                           |
| -------------- | ------------------------------------------------- |
| **Data**       | Information we use to teach the computer          |
| **Model**      | The program that learns from the data             |
| **Training**   | The process of learning from data                 |
| **Prediction** | The output or decision made by the model          |
| **Features**   | Input values (e.g., attendance, assignment marks) |
| **Label**      | The correct answer (e.g., final exam score)       |

---

### 5️⃣ **Mini Project: Predicting Final Exam Scores**

We’ll build a simple machine learning model using Python.

#### 🧪 Problem:

Predict a student’s final grade using:

* Attendance
* Assignment score
* Midterm exam score

#### ✅ Step-by-step Code

**Step 1: Import Required Libraries**

```python
import pandas as pd
from sklearn.linear_model import LinearRegression
```

**Step 2: Create Sample Dataset**

```python
data = {
    'Attendance': [90, 80, 60, 95, 70],
    'Assignment': [85, 75, 65, 90, 60],
    'Midterm': [88, 70, 60, 95, 65],
    'FinalGrade': [90, 78, 65, 95, 70]
}

df = pd.DataFrame(data)
```

**Step 3: Split Features and Label**

```python
X = df[['Attendance', 'Assignment', 'Midterm']]  # Inputs
y = df['FinalGrade']                             # Output
```

**Step 4: Train the Model**

```python
model = LinearRegression()
model.fit(X, y)
```

**Step 5: Predict New Data**

```python
new_student = [[85, 80, 82]]
predicted_grade = model.predict(new_student)
print("Predicted Final Grade:", predicted_grade[0])
```

#### 📌 Expected Output:

```
Predicted Final Grade: 85.2
```

---

### ✅ **Summary of Lecture 1**

* ML is a way to make computers learn from data
* It is used in many areas of life
* You learned basic ML terms
* You built your first ML model in Python to predict exam grades!

---

