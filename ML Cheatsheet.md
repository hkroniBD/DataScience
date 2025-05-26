
## 📘 **Machine Learning Cheat Sheet (Tabular Format)**

**Instructor:** HK Roni, EEE, HSTU
**Audience:** Non-IT / Beginner Level

| 🔢 **Concept**            | 📄 **Description**                                                            | 📌 **Examples**                             | 🧠 **Common Algorithms**                          |
| ------------------------- | ----------------------------------------------------------------------------- | ------------------------------------------- | ------------------------------------------------- |
| **Supervised Learning**   | Train on labeled data (X ➝ Y)                                                 | Predict marks, disease, price               | Linear Regression, Decision Tree, SVM, KNN        |
| **Unsupervised Learning** | Discover patterns from unlabeled data                                         | Customer segmentation, anomaly detection    | K-Means, Hierarchical Clustering, PCA             |
| **Regression**            | Predict continuous numerical values                                           | House price, temperature prediction         | Linear Regression, Decision Tree (Regressor)      |
| **Classification**        | Predict categories or classes                                                 | Spam detection, pass/fail                   | Logistic Regression, SVM, Random Forest           |
| **Clustering**            | Group data without known labels                                               | Market segmentation, document grouping      | K-Means, DBSCAN, Agglomerative Clustering         |
| **Features (X)**          | Input variables or attributes used for prediction                             | Age, Hours Studied, Glucose Level           | Selected manually or with feature selection tools |
| **Labels (Y)**            | Output variable (what to predict)                                             | Pass/Fail, Diabetic/Non-Diabetic            | -                                                 |
| **Train/Test Split**      | Divide data into training and testing sets                                    | Usually 70% train, 30% test                 | `train_test_split()` from scikit-learn            |
| **Overfitting**           | Model fits training data too well but performs poorly on new data             | Learns noise, poor generalization           | Use cross-validation, simpler models              |
| **Underfitting**          | Model is too simple, misses trends in the data                                | Low accuracy on both training and test data | Try complex models, add features                  |
| **Accuracy**              | (Correct predictions / Total predictions)                                     | Useful for classification                   | `accuracy_score()` from sklearn                   |
| **Confusion Matrix**      | Table showing TP, FP, TN, FN                                                  | Helps visualize classifier performance      | `confusion_matrix()` from sklearn                 |
| **Feature Scaling**       | Normalize or standardize input features                                       | Especially needed in KNN, SVM               | MinMaxScaler, StandardScaler                      |
| **Cross-validation**      | Evaluate model using multiple train-test splits                               | Prevents overfitting                        | `cross_val_score()`                               |
| **Pipeline**              | Sequence of data preprocessing + model training steps                         | Makes ML workflow clean and organized       | `Pipeline()` from sklearn                         |
| **Hyperparameter Tuning** | Adjust model settings (e.g., max\_depth, n\_neighbors) to improve performance | GridSearchCV, RandomizedSearchCV            |                                                   |

---

## 📚 **Common Algorithms with Use Cases**

| 🧠 **Algorithm**          | 📂 **Type**                   | 📌 **Best For**                       | 🧪 **Example**                      |
| ------------------------- | ----------------------------- | ------------------------------------- | ----------------------------------- |
| **Linear Regression**     | Supervised (Regression)       | Predicting numeric values             | House price prediction              |
| **Logistic Regression**   | Supervised (Classification)   | Binary outcomes                       | Pass/Fail, Disease prediction       |
| **Decision Tree**         | Supervised (Both)             | Easy to explain, visual               | Student result prediction           |
| **Random Forest**         | Supervised (Both)             | Accurate, reduces overfitting         | Spam detection, credit scoring      |
| **K-Nearest Neighbors**   | Supervised (Both)             | Simple, works well with small data    | Recommend food based on preferences |
| **SVM (Support Vector)**  | Supervised (Both)             | Works well with high-dimensional data | Email classification                |
| **K-Means**               | Unsupervised (Clustering)     | Grouping similar data points          | Customer segmentation               |
| **PCA (Principal Comp.)** | Unsupervised (Dim. Reduction) | Reduce number of features             | Visualize high-dimensional data     |

---

## 🛠️ **Popular Python Functions (scikit-learn)**

| 🧩 **Function**           | 💡 **Purpose**                         |
| ------------------------- | -------------------------------------- |
| `train_test_split()`      | Split data into train and test         |
| `fit()` / `predict()`     | Train model / Make prediction          |
| `accuracy_score()`        | Check how many predictions are correct |
| `confusion_matrix()`      | Evaluate classification performance    |
| `StandardScaler()`        | Standardize features                   |
| `Pipeline()`              | Create a sequence of steps             |
| `GridSearchCV()`          | Try different parameter values         |
| `plot_tree()`             | Visualize decision tree                |
| `classification_report()` | Show precision, recall, f1-score       |

---

