# **Lecture 2: Supervised Learning - Regression & Classification**  
**Duration:** 1.5 Hours  
**Objective:**  
- Understand supervised learning in depth.  
- Learn regression and classification algorithms.  
- Implement models using real-world datasets.  
- Evaluate model performance.  

---

## **Part 1: Recap & Introduction (10 min)**  
### **1.1 Review of Lecture 1**  
- What is Machine Learning?  
- Types of ML: Supervised, Unsupervised, Reinforcement.  
- When to use ML?  

### **1.2 Focus of Lecture 2**  
- **Supervised Learning**: Regression & Classification.  
- Hands-on coding (Python).  

---

## **Part 2: Regression (30 min)**  
### **2.1 What is Regression?**  
- **Goal**: Predict continuous values (e.g., house prices, temperature).  
- **Examples**:  
  - Predicting stock prices.  
  - Estimating sales revenue.  

### **2.2 Linear Regression**  
- **Concept**: Fit a straight line to data (`y = mx + b`).  
- **Assumptions**:  
  - Linear relationship between X and y.  
  - Low multicollinearity.  

#### **Demo: House Price Prediction**  
```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error

# Load dataset (e.g., Boston Housing)
X, y = load_data()
model = LinearRegression()
model.fit(X_train, y_train)
predictions = model.predict(X_test)

# Evaluate
mse = mean_squared_error(y_test, predictions)
print(f"Mean Squared Error: {mse}")
```

### **2.3 Polynomial Regression**  
- **Use Case**: Non-linear relationships (e.g., growth curves).  
- **Code**:  
```python
from sklearn.preprocessing import PolynomialFeatures

poly = PolynomialFeatures(degree=2)
X_poly = poly.fit_transform(X)
model.fit(X_poly, y)
```

---

## **Part 3: Classification (30 min)**  
### **3.1 What is Classification?**  
- **Goal**: Predict categories (e.g., spam/not spam, disease diagnosis).  
- **Examples**:  
  - Email spam detection.  
  - Medical diagnosis (cancer: yes/no).  

### **3.2 Logistic Regression**  
- **Concept**: Predicts probabilities (0 to 1) using the sigmoid function.  
- **Code**:  
```python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()
model.fit(X_train, y_train)
predictions = model.predict(X_test)
```

### **3.3 Decision Trees & Random Forest**  
- **Decision Trees**:  
  - Splits data into branches based on features.  
  - **Code**:  
  ```python
  from sklearn.tree import DecisionTreeClassifier
  model = DecisionTreeClassifier()
  model.fit(X_train, y_train)
  ```  

- **Random Forest**:  
  - Ensemble of decision trees (improves accuracy).  
  - **Code**:  
  ```python
  from sklearn.ensemble import RandomForestClassifier
  model = RandomForestClassifier(n_estimators=100)
  model.fit(X_train, y_train)
  ```

---

## **Part 4: Model Evaluation (20 min)**  
### **4.1 Regression Metrics**  
- **Mean Squared Error (MSE)**: Lower = better.  
- **R-squared (R²)**: 0 to 1 (higher = better fit).  

### **4.2 Classification Metrics**  
- **Confusion Matrix**:  
  - True Positives (TP), False Positives (FP), etc.  
- **Accuracy, Precision, Recall, F1-Score**:  
  ```python
  from sklearn.metrics import classification_report
  print(classification_report(y_test, predictions))
  ```

#### **Demo: Model Evaluation**  
```python
# For classification
from sklearn.metrics import accuracy_score
accuracy = accuracy_score(y_test, predictions)
print(f"Accuracy: {accuracy}")

# For regression
from sklearn.metrics import r2_score
r2 = r2_score(y_test, predictions)
print(f"R-squared: {r2}")
```

---

## **Part 5: Summary & Q&A (10 min)**  
### **Key Takeaways**:  
- **Regression**: Predict numbers (Linear, Polynomial).  
- **Classification**: Predict categories (Logistic Regression, Decision Trees).  
- **Evaluation**: MSE/R² (Regression), Accuracy/Precision (Classification).  

### **Q&A**:  
- When to use Logistic vs. Linear Regression?  
- Why Random Forest over Decision Trees?  

### **Preview Next Lecture**:  
- **Unsupervised Learning (Clustering & Dimensionality Reduction)**.  
- **Lab**: K-Means Clustering.  

---

### **Lecture Materials**:  
- Jupyter Notebook with code examples.  
- Datasets: Boston Housing, Iris, Pima Diabetes.  
- Cheat sheet: Regression vs. Classification.  

**End of Lecture 2** 🚀  

---
