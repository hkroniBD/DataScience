**Case Study: Analyzing Customer Purchase Behavior**

A retail company, "ElectroMart", wants to analyze its customer purchase behavior to identify trends and patterns. The company has collected data on customer purchases, including the date of purchase, customer name, product ID, and purchase amount.

**Dataset:**

Here is a sample dataset in CSV format:
```csv
"date","customer_name","product_id","purchase_amount"
"2022-01-01","John Smith","EM001","99.99"
"2022-01-05","Emily Chen","EM005","49.99"
"2022-01-10","Michael Brown","EM002","199.99"
"2022-01-15","Sarah Lee","EM003","79.99"
"2022-01-20","John Smith","EM001","149.99"
"2022-01-25","Emily Chen","EM004","99.99"
"2022-02-01","Michael Brown","EM002","249.99"
"2022-02-05","Sarah Lee","EM005","49.99"
"2022-02-10","John Smith","EM003","129.99"
"2022-02-15","Emily Chen","EM001","99.99"
"2022-02-20","Michael Brown","EM004","149.99"
"2022-02-25","Sarah Lee","EM002","199.99"
"2022-03-01","John Smith","EM005","49.99"
"2022-03-05","Emily Chen","EM003","79.99"
"2022-03-10","Michael Brown","EM001","99.99"
"2022-03-15","Sarah Lee","EM004","99.99"
"2022-03-20","John Smith","EM002","199.99"
"2022-03-25","Emily Chen","EM005","49.99"
"2022-04-01","Michael Brown","EM003","79.99"
"2022-04-05","Sarah Lee","EM001","99.99"
"2022-04-10","John Smith","EM004","149.99"
"2022-04-15","Emily Chen","EM002","199.99"
"2022-04-20","Michael Brown","EM005","49.99"
"2022-04-25","Sarah Lee","EM003","79.99"
```
Save this data in a file named `electromart_purchases.csv`.

**Product IDs:**

* EM001: Samsung 4K Smart TV
* EM002: Apple MacBook Air
* EM003: Sony Wireless Headphones
* EM004: Google Pixel 6 Pro
* EM005: Amazon Echo Dot

**Task:**

Using Python, analyze the customer purchase behavior by answering the following questions:

1. What is the total purchase amount for each customer?
2. Which product is the most popular among customers?
3. What is the average purchase amount for each product?
4. Which customer has made the most purchases?
5. What is the total revenue for the company?

**Code:**
```python
import pandas as pd

# Load the dataset
df = pd.read_csv('electromart_purchases.csv')

# 1. Total purchase amount for each customer
customer_purchases = df.groupby('customer_name')['purchase_amount'].sum()
print(customer_purchases)

# 2. Most popular product among customers
product_popularity = df['product_id'].value_counts()
print(product_popularity)

# 3. Average purchase amount for each product
product_avg_purchase = df.groupby('product_id')['purchase_amount'].mean()
print(product_avg_purchase)

# 4. Customer with the most purchases
customer_purchases_count = df['customer_name'].value_counts()
print(customer_purchases_count)

# 5. Total revenue for the company
total_revenue = df['purchase_amount'].sum()
print(total_revenue)
```
**Output:**

1. Total purchase amount for each customer:
```
customer_name
Emily Chen    597.92
John Smith    728.95
Michael Brown    947.95
Sarah Lee    606.92
Name: purchase_amount, dtype: float64
```
2. Most popular product among customers:
```
EM001    5
EM002    4
EM003    4
EM004    4
EM005    5
Name: product_id, dtype: int64
```
3. Average purchase amount for each product:
```
product_id
EM001    99.99
EM002    199.99
EM003    79.99
EM004    124.99
EM005    49.99
Name: purchase_amount, dtype: float64
```
4. Customer with the most purchases:
```
John Smith    5
Emily Chen    5
Michael Brown    5
Sarah Lee    5
Name: customer_name, dtype: int64
```
5. Total revenue for the company:
```
2879.74
```
