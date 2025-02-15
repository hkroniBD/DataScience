### **Lecture 11: Pandas Tutorial**

---

### **1. Introduction to Pandas**

**Pandas** is a powerful, fast, and flexible open-source data analysis and manipulation library in Python. It is built on top of NumPy and is designed for working with structured data, such as tables or spreadsheets. Pandas provides two primary data structures: **Series** and **DataFrame**.

---

### **2. Python | Pandas DataFrame**

A **DataFrame** is a 2-dimensional labeled data structure that can hold data of different types (e.g., integers, floats, strings, etc.). It is similar to a table in a database or an Excel spreadsheet, where data is organized in rows and columns.

#### **2.1 Creating a Pandas DataFrame**
You can create a DataFrame from various sources like dictionaries, lists, NumPy arrays, and external files (CSV, Excel, etc.).

**Example 1: Creating a DataFrame from a Dictionary**
```python
import pandas as pd

data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'City': ['New York', 'Los Angeles', 'Chicago']
}

df = pd.DataFrame(data)
print(df)
```

**Example 2: Creating a DataFrame from a List of Lists**
```python
data = [['Alice', 25, 'New York'], ['Bob', 30, 'Los Angeles'], ['Charlie', 35, 'Chicago']]
df = pd.DataFrame(data, columns=['Name', 'Age', 'City'])
print(df)
```

---

### **3. Dealing with Rows and Columns in Pandas DataFrame**

You can access and manipulate rows and columns in a DataFrame easily using indexing.

#### **3.1 Accessing Columns**
```python
# Accessing a single column
print(df['Name'])

# Accessing multiple columns
print(df[['Name', 'Age']])
```

#### **3.2 Accessing Rows**
You can use the `loc[]` and `iloc[]` methods to access rows by label or index position, respectively.

```python
# Accessing a row by index label
print(df.loc[1])  # Accessing the second row

# Accessing a row by index position
print(df.iloc[1])  # Accessing the second row
```

#### **3.3 Adding and Dropping Columns**
```python
# Adding a new column
df['Country'] = ['USA', 'USA', 'USA']

# Dropping a column
df = df.drop('Country', axis=1)
```

---

### **4. Indexing and Selecting Data with Pandas**

Pandas offers multiple ways to index and select data:

#### **4.1 Using `loc[]` and `iloc[]`**
- `loc[]` is used for label-based indexing.
- `iloc[]` is used for integer-based indexing.

```python
# Selecting rows and columns using loc
print(df.loc[0, 'Name'])  # Accessing a specific value

# Selecting multiple rows and columns using loc
print(df.loc[0:2, ['Name', 'Age']])
```

```python
# Using iloc for integer-based indexing
print(df.iloc[0, 1])  # Accessing value at the first row, second column
```

#### **4.2 Selecting Data Based on Conditions**
```python
# Filtering rows based on a condition
print(df[df['Age'] > 30])
```

---

### **5. Boolean Indexing in Pandas**

**Boolean indexing** allows you to filter data based on conditions, producing a DataFrame or Series containing only the rows that satisfy the condition.

```python
# Example: Filtering DataFrame where Age > 30
filtered_df = df[df['Age'] > 30]
print(filtered_df)
```

---

### **6. Conversion Functions in Pandas DataFrame**

Pandas provides functions to convert data from one format to another:

#### **6.1 Converting Columns to Different Data Types**
```python
# Converting column to a specific data type
df['Age'] = df['Age'].astype(float)
```

#### **6.2 Converting a DataFrame to a NumPy Array**
```python
array = df.to_numpy()
print(array)
```

#### **6.3 Converting a DataFrame to a CSV File**
```python
df.to_csv('data.csv', index=False)
```

---

### **7. Iterating over Rows and Columns in Pandas DataFrame**

Pandas provides several ways to iterate over rows and columns.

#### **7.1 Iterating over Rows with `iterrows()`**
```python
for index, row in df.iterrows():
    print(f"Index: {index}, Name: {row['Name']}, Age: {row['Age']}")
```

#### **7.2 Iterating over Columns**
```python
for col in df.columns:
    print(f"Column: {col}")
```

---

### **8. Working with Missing Data in Pandas**

Missing data is common in real-world datasets. Pandas provides several ways to handle missing data.

#### **8.1 Checking for Missing Data**
```python
# Checking for missing data
print(df.isnull())  # Returns a DataFrame of boolean values
```

#### **8.2 Removing Missing Data**
```python
# Dropping rows with missing values
df = df.dropna()

# Dropping columns with missing values
df = df.dropna(axis=1)
```

#### **8.3 Filling Missing Data**
```python
# Filling missing values with a specific value
df = df.fillna(0)
```

---

### **9. Python | Pandas Series**

A **Series** is a one-dimensional labeled array capable of holding any data type. A DataFrame is essentially a collection of Series objects.

#### **9.1 Creating a Pandas Series**
```python
# Creating a Series
s = pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])
print(s)
```

#### **9.2 Accessing Data in a Series**
```python
# Accessing elements by index
print(s['a'])
```

---

### **10. Data Analysis Using Pandas**

Pandas provides powerful tools for data analysis, such as grouping, aggregation, and summarization.

#### **10.1 Grouping Data**
```python
# Grouping by a column and applying an aggregate function
grouped = df.groupby('City').mean()
print(grouped)
```

#### **10.2 Aggregation Functions**
```python
# Applying aggregation functions like sum, mean, count, etc.
print(df['Age'].sum())  # Sum of 'Age' column
print(df['Age'].mean())  # Mean of 'Age' column
```

---

### **11. Read CSV Using `pandas.read_csv()`**

Pandas makes it easy to read CSV files and load the data into a DataFrame.

```python
# Reading a CSV file into a DataFrame
df = pd.read_csv('file.csv')

# Displaying the first few rows of the DataFrame
print(df.head())
```

---

### **Quiz**

1. **Which method would you use to create a DataFrame from a dictionary?**

    a) `pd.Series()`  
    b) `pd.DataFrame()`  
    c) `pd.create()`  
    d) `pd.read_csv()`

2. **Which function in Pandas can be used to read a CSV file into a DataFrame?**

    a) `pd.read_excel()`  
    b) `pd.read_csv()`  
    c) `pd.load_csv()`  
    d) `pd.open_csv()`

3. **How can you filter rows in a DataFrame where the `Age` column is greater than 30?**

    a) `df.where(df['Age'] > 30)`  
    b) `df[df['Age'] > 30]`  
    c) `df.filter(df['Age'] > 30)`  
    d) `df.select(df['Age'] > 30)`

4. **What method is used to convert a DataFrame column to a specific data type?**

    a) `df.convert()`  
    b) `df.astype()`  
    c) `df.to_type()`  
    d) `df.to_format()`

5. **Which method would you use to iterate over rows in a Pandas DataFrame?**

    a) `df.iterrows()`  
    b) `df.iter()`  
    c) `df.rows()`  
    d) `df.row_iter()`

---

### **Answer Key**

1. **b) `pd.DataFrame()`**
2. **b) `pd.read_csv()`**
3. **b) `df[df['Age'] > 30]`**
4. **b) `df.astype()`**
5. **a) `df.iterrows()`**

---

### **Summary**

In this lecture, we covered:
1. **Pandas DataFrame**: Understanding how to create, access, and manipulate DataFrames.
2. **Rows and Columns**: How to add, drop, and access data within rows and columns.
3. **Indexing and Selecting Data**: Techniques for selecting data based on labels, positions, and conditions.
4. **Boolean Indexing**: Filtering data using boolean conditions.
5. **Missing Data Handling**: Managing missing data through removal or imputation.
6. **Pandas Series**: Working with one-dimensional data.
7. **Data Analysis**: Using aggregation and group-by functions for analysis.
8. **Reading CSV Files**: Importing data from CSV files into DataFrames.

Pandas is an essential tool for data manipulation and analysis, enabling efficient handling of structured data.
