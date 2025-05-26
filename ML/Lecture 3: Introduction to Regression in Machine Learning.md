## 🎓 **Lecture 3: Introduction to Regression in Machine Learning**


**Instructor:** HK Roni, EEE, HSTU

---

### 🗂️ **Lecture Outline**

1. What is Regression?
2. Classification vs. Regression
3. Real-Life Examples of Regression
4. Linear Regression Explained
5. Python Implementation: Predicting House Prices
6. Summary and Homework

---

### 1️⃣ **What is Regression?**

**Regression** is a type of supervised learning where the output is a **real number** (continuous value).

> 🧠 It helps us **predict a value** based on input data.
> Think of predicting:
>
> * A person’s weight from height
> * Final marks from attendance and assignment
> * House price from size

---

### 2️⃣ **Classification vs. Regression**

| Concept | Classification                 | Regression                     |
| ------- | ------------------------------ | ------------------------------ |
| Output  | Category (Pass/Fail, Spam/Not) | Number (marks, price)          |
| Example | Will it rain? Yes or No        | How much will it rain? (in mm) |

---

### 3️⃣ **Real-Life Examples of Regression**

| Scenario               | Input                   | Output                  |
| ---------------------- | ----------------------- | ----------------------- |
| Predicting salary      | Years of experience     | Monthly salary (in BDT) |
| Estimating house price | Size, location          | Price in lakh BDT       |
| Student performance    | Attendance, assignments | Final score             |

---

### 4️⃣ **How Linear Regression Works**

**Linear Regression** fits a straight line between input and output.

🔢 Mathematical form:

```
Y = mX + b
```

Where:

* `X` = Input (e.g., square feet)
* `Y` = Output (e.g., house price)
* `m` = slope (how steep the line is)
* `b` = intercept (where the line starts on Y-axis)

> 📈 It tries to draw a best-fit line through the points (data).

---

### 5️⃣ **Practical Example: Predicting House Price**

We will build a simple model to predict **house prices** based on **house size**.

#### ✅ Python Implementation

**Step 1: Import Required Libraries**

```python
import pandas as pd
from sklearn.linear_model import LinearRegression
import matplotlib.pyplot as plt
```

**Step 2: Prepare Dataset**

```python
data = {
    'Size': [1000, 1200, 1500, 1800, 2000],     # Size in square feet
    'Price': [20, 24, 30, 36, 40]              # Price in lakh BDT
}
df = pd.DataFrame(data)
```

**Step 3: Define Inputs and Outputs**

```python
X = df[['Size']]      # Input feature
y = df['Price']       # Output label
```

**Step 4: Create and Train the Model**

```python
model = LinearRegression()
model.fit(X, y)
```

**Step 5: Make Prediction**

```python
new_size = [[1600]]  # New house size to predict price
predicted_price = model.predict(new_size)
print("Predicted Price (in lakh):", predicted_price[0])
```

#### 📌 Expected Output:

```
Predicted Price (in lakh): 32.0
```

**Step 6: Visualize the Result**

```python
# Draw the original data points
plt.scatter(df['Size'], df['Price'], color='blue', label='Original Data')

# Plot the regression line
plt.plot(df['Size'], model.predict(X), color='red', label='Best Fit Line')

# Highlight the prediction
plt.scatter(1600, predicted_price[0], color='green', label='Prediction')

plt.xlabel("Size (sq ft)")
plt.ylabel("Price (lakh BDT)")
plt.title("Linear Regression: House Price Prediction")
plt.legend()
plt.grid(True)
plt.show()
```

---

### 🔍 Understanding the Prediction

* The model learned from data like (1000 sq ft → 20 lakh)
* For a 1600 sq ft house, it estimates \~32 lakh based on the trend

---

### ✅ **Summary of Lecture 3**

* Regression predicts **numerical values**
* Linear regression finds the **best fit line** for prediction
* You built a regression model to predict house prices from size
* You also **visualized** how the line fits the data

---

### 🧠 **Homework for Students**

1. Add more data points (house size and price) and retrain the model.
2. Try predicting the price of a 2500 sq ft house.
3. Collect real data (even imaginary) from your area and apply the same logic.
4. Try using multiple features like **size, number of rooms, location score**.

---
