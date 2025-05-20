### **Lecture 2: Supervised Learning**

#### **1. Lecture Objectives**

* Define supervised learning and its characteristics
* Differentiate between classification and regression
* Understand key algorithms in supervised learning
* Learn evaluation metrics for supervised models
* Apply concepts to a simple case study using Python (optional)

---

### **2. What is Supervised Learning?**

> **Definition:** Supervised learning is a type of machine learning where the model is trained using labeled data—that is, data that includes both input features and the correct output.

#### **Characteristics**

* Input-output pairs are known
* Goal is to learn a mapping from inputs (X) to outputs (Y)
* Feedback is direct and immediate during training

---

### **3. Types of Supervised Learning**

#### **A. Classification**

* Predict **discrete** labels
* **Examples:**

  * Email spam detection (Spam/Not Spam)
  * Disease diagnosis (Positive/Negative)
* **Common Algorithms:**

  * Logistic Regression
  * k-Nearest Neighbors (k-NN)
  * Decision Trees
  * Support Vector Machines (SVM)
  * Naïve Bayes

#### **B. Regression**

* Predict **continuous** values
* **Examples:**

  * House price prediction
  * Stock market forecasting
* **Common Algorithms:**

  * Linear Regression
  * Polynomial Regression
  * Support Vector Regression (SVR)
  * Decision Tree Regressor

---

### **4. Supervised Learning Workflow**

1. **Data Collection**
2. **Data Preprocessing** (handle missing values, encode categories, scale features)
3. **Split Dataset** (Train/Test split)
4. **Model Training**
5. **Prediction**
6. **Evaluation**

---

### **5. Evaluation Metrics**

#### **For Classification:**

* Accuracy
* Precision, Recall, F1-Score
* Confusion Matrix
* ROC-AUC Curve

#### **For Regression:**

* Mean Absolute Error (MAE)
* Mean Squared Error (MSE)
* Root Mean Squared Error (RMSE)
* R-squared (R²)

---

### **6. Case Study (Simple Python Example)**

You may walk through a basic example using the Iris dataset for classification or Boston housing dataset for regression using `scikit-learn`.

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeClassifier
from sklearn.metrics import accuracy_score

# Load dataset
data = load_iris()
X, y = data.data, data.target

# Split data
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Train model
model = DecisionTreeClassifier()
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

# Evaluate
print("Accuracy:", accuracy_score(y_test, y_pred))
```

---

### **7. Summary**

* Supervised learning uses labeled data to train models
* Two main tasks: classification and regression
* Multiple algorithms are available for each task
* Model performance should be evaluated using appropriate metrics

---

### **8. Assignment**

* Choose a dataset (e.g., from Kaggle or UCI Repository)
* Perform a basic classification or regression task
* Submit a brief report with your code and performance metrics

---


