## 🎓 **Lecture 5: Data Preprocessing in Machine Learning**

**Instructor:** HK Roni, EEE, HSTU

---

### 🗂️ **Lecture Outline**

1. Why Data Preprocessing is Important
2. Common Preprocessing Steps
3. Handling Missing Data
4. Feature Scaling
5. Encoding Categorical Data
6. Python Example
7. Summary and Homework

---

### 1️⃣ **Why Data Preprocessing is Important**

Machine learning models work with **clean and numeric data**.

> Real-world data is often **messy, incomplete, and inconsistent**.
> Preprocessing prepares it for better model accuracy and performance.

---

### 2️⃣ **Common Preprocessing Steps**

| Step                  | Description                             |
| --------------------- | --------------------------------------- |
| Handling Missing Data | Filling in or removing empty values     |
| Feature Scaling       | Ensuring features are on the same scale |
| Encoding              | Converting categories to numbers        |
| Splitting Dataset     | Dividing into training and testing data |

---

### 3️⃣ **Handling Missing Data**

#### 📌 Example:

```python
import pandas as pd
import numpy as np

data = {
    'Height': [160, 170, np.nan, 180],
    'Weight': [55, 65, 70, np.nan]
}
df = pd.DataFrame(data)
```

**Fill missing values using mean:**

```python
df['Height'].fillna(df['Height'].mean(), inplace=True)
df['Weight'].fillna(df['Weight'].mean(), inplace=True)
print(df)
```

---

### 4️⃣ **Feature Scaling (Normalization)**

Different units can confuse the model (e.g., cm vs kg).
We scale features so that they have **similar ranges**.

#### Using MinMaxScaler:

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()
scaled_data = scaler.fit_transform(df)
print(scaled_data)
```

---

### 5️⃣ **Encoding Categorical Data**

Machine learning models don’t understand text like “Male” or “Female”.
We convert it into numbers using **Label Encoding** or **One-Hot Encoding**.

#### Label Encoding:

```python
from sklearn.preprocessing import LabelEncoder

gender = ['Male', 'Female', 'Female', 'Male']
le = LabelEncoder()
encoded = le.fit_transform(gender)
print(encoded)
# Output: [1 0 0 1]
```

---

### 6️⃣ **Complete Python Example**

Let’s combine all in one:

```python
import pandas as pd
import numpy as np
from sklearn.preprocessing import MinMaxScaler, LabelEncoder

# Create dataset
data = {
    'Height': [160, 170, np.nan, 180],
    'Weight': [55, 65, 70, np.nan],
    'Gender': ['Male', 'Female', 'Female', 'Male']
}

df = pd.DataFrame(data)

# Handle missing data
df['Height'].fillna(df['Height'].mean(), inplace=True)
df['Weight'].fillna(df['Weight'].mean(), inplace=True)

# Encode gender
le = LabelEncoder()
df['Gender'] = le.fit_transform(df['Gender'])  # Male=1, Female=0

# Scale features
scaler = MinMaxScaler()
scaled = scaler.fit_transform(df)

# Show scaled result
scaled_df = pd.DataFrame(scaled, columns=['Height', 'Weight', 'Gender'])
print(scaled_df)
```

---

### ✅ Output Snapshot (example):

```
   Height    Weight   Gender
0  0.00000  0.000000     1.0
1  0.33333  0.500000     0.0
2  0.50000  1.000000     0.0
3  1.00000  0.583333     1.0
```

---

### ✅ **Summary of Lecture 5**

* Preprocessing makes raw data ready for ML models
* Missing values must be handled
* Categorical text must be converted to numbers
* Feature scaling improves accuracy and training speed
* Python tools like `pandas`, `LabelEncoder`, and `MinMaxScaler` make this easy

---

### 🧠 Homework

1. Create a dataset with height, weight, and gender of 10 people.
2. Add some missing values and try to clean them.
3. Encode gender and scale all features.
4. Visualize the original vs scaled data using bar charts.
