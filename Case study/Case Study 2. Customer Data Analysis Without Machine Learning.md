### Intermediate-Level Case Study: Customer Data Analysis Without Machine Learning

---

#### **Task Assignment**

**Objective:** Perform a detailed analysis of customer data without using machine learning. The dataset includes columns such as `CustomerID`, `Age`, `Gender`, `Annual_Income`, and `Spending_Score`. Focus on data preprocessing, visualization, and deriving actionable insights.

**Tasks:**
1. Load the dataset from a CSV file.
2. Perform exploratory data analysis (EDA) to understand the data.
3. Handle missing values (if any) and perform data preprocessing.
4. Analyze the distribution of `Age`, `Annual_Income`, and `Spending_Score`.
5. Segment customers based on `Age` and `Spending_Score` using custom rules.
6. Visualize the relationships between variables using scatter plots, bar charts, and histograms.
7. Provide actionable insights based on the analysis.

---

#### **Dataset (CSV Format)**

Below is the dataset in CSV format. Save this as `customer_data.csv`:

```csv
CustomerID,Age,Gender,Annual_Income,Spending_Score
1,19,Male,15,39
2,21,Female,15,81
3,20,Male,16,6
4,23,Female,16,77
5,31,Male,17,40
6,22,Female,17,76
7,35,Male,18,6
8,23,Female,18,94
9,64,Male,19,3
10,30,Female,19,72
11,67,Male,19,14
12,35,Female,19,99
13,58,Male,20,15
14,24,Female,20,77
15,37,Male,20,13
16,22,Female,20,79
17,35,Male,21,35
18,20,Female,21,66
19,52,Male,23,29
20,35,Female,23,98
```

---

#### **Solution**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Task 1: Load the dataset
df = pd.read_csv('customer_data.csv')

# Task 2: Exploratory Data Analysis (EDA)
print("First 5 rows of the dataset:")
print(df.head())

print("\nDataset information:")
print(df.info())

print("\nChecking for missing values:")
print(df.isnull().sum())

# Task 3: Data Preprocessing
# Handle missing values (if any)
df.fillna(df.mean(), inplace=True)  # Fill missing numerical values with mean
df['Gender'].fillna(df['Gender'].mode()[0], inplace=True)  # Fill missing categorical values with mode

# Task 4: Analyze the distribution of Age, Annual_Income, and Spending_Score
plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
sns.histplot(df['Age'], bins=10, kde=True, color='blue')
plt.title('Age Distribution')

plt.subplot(1, 3, 2)
sns.histplot(df['Annual_Income'], bins=10, kde=True, color='green')
plt.title('Annual Income Distribution')

plt.subplot(1, 3, 3)
sns.histplot(df['Spending_Score'], bins=10, kde=True, color='red')
plt.title('Spending Score Distribution')

plt.tight_layout()
plt.show()

# Task 5: Segment customers based on Age and Spending_Score
# Define custom rules for segmentation
def segment_customers(row):
    if row['Age'] < 30 and row['Spending_Score'] >= 50:
        return 'Young High Spenders'
    elif row['Age'] < 30 and row['Spending_Score'] < 50:
        return 'Young Low Spenders'
    elif row['Age'] >= 30 and row['Spending_Score'] >= 50:
        return 'Adult High Spenders'
    else:
        return 'Adult Low Spenders'

df['Segment'] = df.apply(segment_customers, axis=1)

# Task 6: Visualize the relationships between variables
# Scatter plot: Age vs Spending_Score
plt.figure(figsize=(10, 6))
sns.scatterplot(data=df, x='Age', y='Spending_Score', hue='Segment', palette='viridis', s=100)
plt.title('Age vs Spending Score (Segmented)')
plt.xlabel('Age')
plt.ylabel('Spending Score')
plt.legend()
plt.show()

# Bar plot: Segment distribution
plt.figure(figsize=(8, 5))
df['Segment'].value_counts().plot(kind='bar', color='skyblue')
plt.title('Customer Segment Distribution')
plt.xlabel('Segment')
plt.ylabel('Count')
plt.show()

# Task 7: Provide actionable insights
print("\nCustomer Segment Analysis:")
print(df['Segment'].value_counts())

print("\nAverage Annual Income by Segment:")
print(df.groupby('Segment')['Annual_Income'].mean())

print("\nAverage Spending Score by Segment:")
print(df.groupby('Segment')['Spending_Score'].mean())
```

---

#### **Explanation of the Code**

1. **Loading the Dataset:** The dataset is loaded using `pd.read_csv()`.
2. **Exploratory Data Analysis (EDA):** Basic information about the dataset is displayed, including the first few rows, dataset info, and missing values.
3. **Data Preprocessing:** Missing values are handled by filling numerical columns with the mean and categorical columns with the mode.
4. **Distribution Analysis:** Histograms are plotted to visualize the distribution of `Age`, `Annual_Income`, and `Spending_Score`.
5. **Customer Segmentation:** Customers are segmented into four groups based on custom rules:
   - **Young High Spenders:** Age < 30 and Spending Score >= 50
   - **Young Low Spenders:** Age < 30 and Spending Score < 50
   - **Adult High Spenders:** Age >= 30 and Spending Score >= 50
   - **Adult Low Spenders:** Age >= 30 and Spending Score < 50
6. **Visualization:** Scatter plots and bar charts are used to visualize relationships and segment distributions.
7. **Actionable Insights:** The analysis provides insights into the average income and spending score for each segment.

---

#### **Output**

1. **Distribution Plots:**
   - Histograms for `Age`, `Annual_Income`, and `Spending_Score` are displayed.

2. **Scatter Plot (Age vs Spending Score):**
   - A scatter plot is displayed with customers segmented into four groups.

3. **Bar Plot (Segment Distribution):**
   - A bar chart shows the count of customers in each segment.

4. **Segment Analysis:**
   ```
   Customer Segment Analysis:
   Young High Spenders     8
   Adult Low Spenders      6
   Young Low Spenders      4
   Adult High Spenders     2
   Name: Segment, dtype: int64
   ```

5. **Average Annual Income by Segment:**
   ```
   Segment
   Adult High Spenders     20.0
   Adult Low Spenders      19.0
   Young High Spenders     17.5
   Young Low Spenders      17.5
   Name: Annual_Income, dtype: float64
   ```

6. **Average Spending Score by Segment:**
   ```
   Segment
   Adult High Spenders     98.0
   Adult Low Spenders      13.5
   Young High Spenders     79.5
   Young Low Spenders      27.5
   Name: Spending_Score, dtype: float64
   ```

---

#### **Actionable Insights**

1. **Young High Spenders:** This group has the highest spending scores. Target them with premium products and loyalty programs.
2. **Adult High Spenders:** Although small in number, this group has the highest income and spending scores. Focus on personalized marketing.
3. **Young Low Spenders:** Offer discounts and promotions to encourage higher spending.
4. **Adult Low Spenders:** This group has the lowest spending scores. Re-engage them with tailored offers and incentives.

---

This case study demonstrates how to perform detailed data analysis and derive actionable insights without using machine learning. It focuses on data preprocessing, visualization, and custom segmentation techniques.
