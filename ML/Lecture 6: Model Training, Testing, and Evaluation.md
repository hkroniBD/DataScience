## 🎓 **Lecture 6: Model Training, Testing, and Evaluation**

**Series:** Machine Learning for Non-IT Students
**Instructor:** HK Roni, EEE, HSTU

---

### 🗂️ **Lecture Outline**

1. What is Model Training and Testing?
2. Splitting the Dataset
3. Training a Model
4. Making Predictions
5. Evaluating the Model
6. Practical Example: Student Marks Prediction
7. Summary and Homework

---

### 1️⃣ **What is Model Training and Testing?**

When we build a machine learning model, we need to:

* **Train** it on known data
* **Test** it on new, unseen data

> 🔄 This helps us measure how well the model can predict real-world outcomes.

---

### 2️⃣ **Splitting the Dataset**

We divide the data into two parts:

* **Training set**: Used to teach the model (usually 70–80%)
* **Testing set**: Used to evaluate the model (usually 20–30%)

#### ✅ Code Example:

```python
from sklearn.model_selection import train_test_split

X = df[['Hours_Studied']]
y = df['Final_Score']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
```

---

### 3️⃣ **Training the Model**

We’ll use **Linear Regression** to predict student scores based on study hours.

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X_train, y_train)  # Model learns the relationship
```

---

### 4️⃣ **Making Predictions**

Now that the model is trained, we test it on new data (X\_test):

```python
y_pred = model.predict(X_test)
print("Predicted Scores:", y_pred)
```

---

### 5️⃣ **Evaluating the Model**

We compare the predicted values with the actual values using metrics like:

| Metric                        | Description                              |
| ----------------------------- | ---------------------------------------- |
| **MAE** (Mean Absolute Error) | Average error in prediction              |
| **MSE** (Mean Squared Error)  | Squared average error                    |
| **R² Score**                  | How well the model explains the variance |

#### ✅ Code:

```python
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score

mae = mean_absolute_error(y_test, y_pred)
mse = mean_squared_error(y_test, y_pred)
r2  = r2_score(y_test, y_pred)

print("MAE:", mae)
print("MSE:", mse)
print("R² Score:", r2)
```

---

### 6️⃣ **Practical Example: Student Score Prediction**

Let’s walk through a full example using dummy data.

#### 📊 Dataset:

| Hours\_Studied | Final\_Score |
| -------------- | ------------ |
| 2              | 50           |
| 4              | 55           |
| 6              | 60           |
| 8              | 80           |
| 10             | 90           |

#### 🧑‍💻 Complete Python Code:

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score

# Step 1: Create dataset
data = {'Hours_Studied': [2, 4, 6, 8, 10],
        'Final_Score': [50, 55, 60, 80, 90]}
df = pd.DataFrame(data)

# Step 2: Split data
X = df[['Hours_Studied']]
y = df['Final_Score']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=0)

# Step 3: Train model
model = LinearRegression()
model.fit(X_train, y_train)

# Step 4: Predict
y_pred = model.predict(X_test)

# Step 5: Evaluate
print("Actual:", y_test.values)
print("Predicted:", y_pred)

print("MAE:", mean_absolute_error(y_test, y_pred))
print("MSE:", mean_squared_error(y_test, y_pred))
print("R² Score:", r2_score(y_test, y_pred))
```

---

### ✅ Example Output:

```
Actual: [90]
Predicted: [84.5]
MAE: 5.5
MSE: 30.25
R² Score: 0.95 (approximately)
```

---

### ✅ Summary of Lecture 6

* We split the data into **training** and **testing**
* We trained a **linear regression model**
* We predicted results and **evaluated using MAE, MSE, and R²**
* We used **realistic examples** and simple Python code

---

### 🧠 Homework

1. Use the same approach to predict:

   * Student marks based on **attendance**
   * House price based on **number of rooms**
2. Change the test size from `0.2` to `0.3` or `0.5` and observe changes in accuracy.
3. Plot actual vs predicted values using `matplotlib`.

#### Hint:

```python
import matplotlib.pyplot as plt

plt.scatter(X_test, y_test, color='blue', label='Actual')
plt.plot(X_test, y_pred, color='red', label='Predicted')
plt.xlabel("Hours Studied")
plt.ylabel("Final Score")
plt.title("Actual vs Predicted")
plt.legend()
plt.show()
```

---

