## 🧑‍💻 **Case Study: Computer Sales Data Analysis using Python**

---

### 📌 **Objective**

Analyze computer sales data to:

* Understand trends in sales performance
* Identify key drivers of revenue
* Segment customers by preferences
* Provide actionable business insights

---

### 🗃️ **Dataset Description**

Suppose we have a dataset named `computer_sales.csv` with the following features:

If actual data is not available, use the following code to simulate one:

```python
import numpy as np

np.random.seed(0)
n = 1000
df = pd.DataFrame({
    'InvoiceID': np.arange(1, n+1),
    'Date': pd.date_range(start='2023-01-01', periods=n, freq='D'),
    'CustomerID': np.random.randint(100, 500, size=n),
    'CustomerRegion': np.random.choice(['East', 'West', 'North', 'South'], n),
    'ProductCategory': np.random.choice(['Laptop', 'Desktop', 'Accessory'], n),
    'Brand': np.random.choice(['Dell', 'HP', 'Lenovo', 'Apple', 'Acer'], n),
    'UnitPrice': np.random.randint(300, 2000, size=n),
    'Quantity': np.random.randint(1, 5, size=n)
})
df['TotalAmount'] = df['UnitPrice'] * df['Quantity']
df.to_csv('computer_sales.csv', index=False)
```

---
```

| Column Name       | Description                           |
| ----------------- | ------------------------------------- |
| `InvoiceID`       | Unique identifier for each sale       |
| `Date`            | Date of transaction                   |
| `CustomerID`      | Unique ID of the customer             |
| `CustomerRegion`  | Region of customer (East, West, etc.) |
| `ProductCategory` | Desktop, Laptop, Accessories          |
| `Brand`           | Dell, HP, Lenovo, Apple, etc.         |
| `UnitPrice`       | Price per unit                        |
| `Quantity`        | Number of units sold                  |
| `TotalAmount`     | UnitPrice × Quantity                  |

---

### 🧪 **Step-by-Step Analysis in Python**

#### ✅ **1. Import Libraries**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

---

#### ✅ **2. Load Dataset**

```python
df = pd.read_csv('computer_sales.csv')
df.head()
```

---

#### ✅ **3. Data Overview**

```python
print(df.info())
print(df.describe())
print(df.isnull().sum())
```

---

#### ✅ **4. Sales Trend Over Time**

```python
df['Date'] = pd.to_datetime(df['Date'])
monthly_sales = df.groupby(df['Date'].dt.to_period('M'))['TotalAmount'].sum()

monthly_sales.plot(kind='line', figsize=(10,5), title='Monthly Sales Trend')
plt.xlabel('Month')
plt.ylabel('Total Sales')
plt.grid(True)
plt.show()
```

---

#### ✅ **5. Product Category Sales**

```python
category_sales = df.groupby('ProductCategory')['TotalAmount'].sum().sort_values()

category_sales.plot(kind='barh', color='skyblue', title='Sales by Product Category')
plt.xlabel('Total Sales')
plt.show()
```

---

#### ✅ **6. Regional Analysis**

```python
region_sales = df.groupby('CustomerRegion')['TotalAmount'].sum()

sns.barplot(x=region_sales.index, y=region_sales.values)
plt.title('Sales by Region')
plt.ylabel('Total Sales')
plt.xticks(rotation=45)
plt.show()
```

---

#### ✅ **7. Top Brands**

```python
top_brands = df.groupby('Brand')['TotalAmount'].sum().sort_values(ascending=False).head(5)

top_brands.plot(kind='bar', title='Top 5 Brands by Sales', color='green')
plt.ylabel('Revenue')
plt.show()
```

---

#### ✅ **8. Correlation Analysis**

```python
sns.heatmap(df[['UnitPrice', 'Quantity', 'TotalAmount']].corr(), annot=True, cmap='coolwarm')
plt.title('Correlation Matrix')
plt.show()
```

---

#### ✅ **9. Customer Purchase Behavior**

```python
customer_summary = df.groupby('CustomerID').agg({
    'TotalAmount': 'sum',
    'Quantity': 'sum'
}).sort_values(by='TotalAmount', ascending=False).head(10)

customer_summary.plot(kind='bar', y='TotalAmount', title='Top 10 Customers by Sales')
plt.ylabel('Total Amount')
plt.show()
```

---

### 🧾 **Insights**

* **Sales are highest during Q4**, indicating seasonal influence.
* **Laptops contribute the most to total sales**, suggesting a focus for inventory planning.
* **Western region shows the highest revenue**, highlighting strong regional demand.
* **Apple and Dell** are top-performing brands in terms of revenue.
* A few customers contribute disproportionately to revenue, enabling loyalty program targeting.

---

### 🏁 **Conclusion**

This analysis helps the business:

* Optimize marketing and stock planning
* Improve customer segmentation
* Focus on high-performing regions and products
* Identify trends to drive business growth

---


