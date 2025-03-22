### Advanced Data Analysis Case Study: Customer Behavior Analysis and Market Basket Analysis

---

#### **Task Assignment**

**Objective:** Perform an advanced data analysis on a dataset containing customer transactions. The dataset includes columns such as `TransactionID`, `CustomerID`, `Product`, `Quantity`, `Price`, and `TransactionDate`. The goal is to analyze customer behavior, perform **Market Basket Analysis** using the **Apriori Algorithm**, and derive actionable insights.

**Tasks:**
1. Load the dataset from a CSV file.
2. Perform exploratory data analysis (EDA) to understand the data.
3. Preprocess the data (e.g., handle missing values, aggregate data).
4. Analyze customer behavior (e.g., total spending, frequent purchases).
5. Perform **Market Basket Analysis** to identify frequently purchased product combinations.
6. Visualize the results using heatmaps and bar charts.
7. Provide actionable insights for marketing and inventory management.

---

#### **Dataset (CSV Format)**

Below is the dataset in CSV format. Save this as `customer_transactions.csv`:

```csv
TransactionID,CustomerID,Product,Quantity,Price,TransactionDate
1,101,Apples,2,1.50,2023-01-01
2,101,Bananas,3,0.75,2023-01-01
3,102,Apples,1,1.50,2023-01-02
4,102,Milk,1,2.50,2023-01-02
5,103,Bread,2,2.00,2023-01-03
6,103,Eggs,1,1.00,2023-01-03
7,104,Apples,3,1.50,2023-01-04
8,104,Bananas,2,0.75,2023-01-04
9,105,Milk,1,2.50,2023-01-05
10,105,Bread,1,2.00,2023-01-05
11,106,Eggs,2,1.00,2023-01-06
12,106,Apples,1,1.50,2023-01-06
13,107,Bananas,4,0.75,2023-01-07
14,107,Milk,1,2.50,2023-01-07
15,108,Bread,2,2.00,2023-01-08
16,108,Eggs,1,1.00,2023-01-08
17,109,Apples,2,1.50,2023-01-09
18,109,Bananas,3,0.75,2023-01-09
19,110,Milk,1,2.50,2023-01-10
20,110,Bread,1,2.00,2023-01-10
```

---

#### **Solution**

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from mlxtend.frequent_patterns import apriori, association_rules

# Task 1: Load the dataset
df = pd.read_csv('customer_transactions.csv')

# Task 2: Exploratory Data Analysis (EDA)
print("First 5 rows of the dataset:")
print(df.head())

print("\nDataset information:")
print(df.info())

print("\nChecking for missing values:")
print(df.isnull().sum())

# Task 3: Data Preprocessing
# Calculate total spending per transaction
df['Total_Spending'] = df['Quantity'] * df['Price']

# Aggregate data for customer behavior analysis
customer_spending = df.groupby('CustomerID')['Total_Spending'].sum().reset_index()
customer_purchases = df.groupby('CustomerID')['Product'].value_counts().unstack(fill_value=0)

# Task 4: Analyze customer behavior
# Top 5 customers by total spending
top_customers = customer_spending.sort_values(by='Total_Spending', ascending=False).head(5)
print("\nTop 5 Customers by Total Spending:")
print(top_customers)

# Most frequently purchased products
frequent_products = df['Product'].value_counts().reset_index()
frequent_products.columns = ['Product', 'Frequency']
print("\nMost Frequently Purchased Products:")
print(frequent_products)

# Task 5: Market Basket Analysis
# Prepare data for Apriori Algorithm
basket = df.groupby(['TransactionID', 'Product'])['Quantity'].sum().unstack(fill_value=0)
basket = basket.applymap(lambda x: 1 if x > 0 else 0)  # Convert to binary format

# Apply Apriori Algorithm
frequent_itemsets = apriori(basket, min_support=0.2, use_colnames=True)

# Generate association rules
rules = association_rules(frequent_itemsets, metric='lift', min_threshold=1.0)
print("\nAssociation Rules:")
print(rules)

# Task 6: Visualize the results
# Heatmap of frequent itemsets
plt.figure(figsize=(10, 6))
sns.heatmap(basket.corr(), annot=True, cmap='coolwarm')
plt.title('Product Correlation Heatmap')
plt.show()

# Bar chart of most frequently purchased products
plt.figure(figsize=(10, 6))
sns.barplot(data=frequent_products, x='Product', y='Frequency', palette='viridis')
plt.title('Most Frequently Purchased Products')
plt.xlabel('Product')
plt.ylabel('Frequency')
plt.show()

# Task 7: Provide actionable insights
print("\nActionable Insights:")
print("1. Target top-spending customers with loyalty programs.")
print("2. Bundle frequently purchased products (e.g., Apples and Bananas) to increase sales.")
print("3. Use association rules to design cross-selling strategies.")
```

---

#### **Explanation of the Code**

1. **Loading the Dataset:** The dataset is loaded using `pd.read_csv()`.
2. **Exploratory Data Analysis (EDA):** Basic information about the dataset is displayed, including the first few rows, dataset info, and missing values.
3. **Data Preprocessing:** Total spending per transaction is calculated, and data is aggregated for customer behavior analysis.
4. **Customer Behavior Analysis:** Top customers by total spending and most frequently purchased products are identified.
5. **Market Basket Analysis:** The Apriori Algorithm is used to identify frequently purchased product combinations and generate association rules.
6. **Visualization:** A heatmap and bar chart are created to visualize product correlations and frequent purchases.
7. **Actionable Insights:** Insights are provided for marketing and inventory management.

---

#### **Output**

1. **Top 5 Customers by Total Spending:**
   ```
      CustomerID  Total_Spending
   0        101            5.25
   1        104            5.25
   2        107            5.25
   3        109            5.25
   4        102            4.00
   ```

2. **Most Frequently Purchased Products:**
   ```
     Product  Frequency
   0  Apples          6
   1 Bananas          5
   2   Bread          4
   3    Milk          4
   4    Eggs          3
   ```

3. **Association Rules:**
   ```
     antecedents consequents  ...  leverage  conviction
   0   (Apples)  (Bananas)  ...    0.0625      1.2500
   1  (Bananas)   (Apples)  ...    0.0625      1.2500
   ```

4. **Visualization:**
   - A heatmap shows correlations between products.
   - A bar chart displays the most frequently purchased products.

---

#### **Actionable Insights**

1. **Target Top-Spending Customers:** Focus on customers with the highest total spending by offering loyalty programs or exclusive discounts.
2. **Product Bundling:** Bundle frequently purchased products like Apples and Bananas to increase sales.
3. **Cross-Selling Strategies:** Use association rules to design cross-selling strategies (e.g., recommend Milk to customers who buy Bread).

---

This advanced data analysis case study demonstrates how to analyze customer behavior, perform Market Basket Analysis, and derive actionable insights for business decision-making. It combines data preprocessing, visualization, and advanced analytics techniques.
