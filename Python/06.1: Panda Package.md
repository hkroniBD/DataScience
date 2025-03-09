### Detailed Lecture on Pandas in Python

---

#### Introduction to Pandas

**Pandas** is a powerful open-source library for data manipulation and analysis in Python. It provides data structures like **Series** (1D) and **DataFrames** (2D) to handle tabular data, time series, and heterogeneous data efficiently. Pandas is widely used for data cleaning, transformation, and analysis in fields like finance, social sciences, and machine learning.

---

#### Key Features of Pandas

1. **DataFrame and Series**: Core data structures for handling tabular data.
2. **Data Alignment**: Automatic alignment of data during operations.
3. **Missing Data Handling**: Tools to detect, remove, or fill missing values.
4. **Reshaping and Pivoting**: Flexible reshaping of datasets.
5. **Grouping and Aggregation**: Split-apply-combine operations.
6. **Time Series**: Support for date/time data manipulation.
7. **I/O Tools**: Read/write data from CSV, Excel, SQL, and more.

---

#### Installation

To install Pandas, use pip:

```bash
pip install pandas
```

---

#### Importing Pandas

```python
import pandas as pd
```

---

#### Pandas Data Structures

1. **Series** (1D labeled array):

   ```python
   # Create a Series from a list
   s = pd.Series([10, 20, 30, 40], name="age")
   print(s)
   ```

   **Output**:
   ```
   0    10
   1    20
   2    30
   3    40
   Name: age, dtype: int64
   ```

2. **DataFrame** (2D labeled data structure):

   ```python
   # Create a DataFrame from a dictionary
   data = {
       "name": ["Alice", "Bob", "Charlie"],
       "age": [25, 30, 35],
       "city": ["New York", "London", "Tokyo"]
   }
   df = pd.DataFrame(data)
   print(df)
   ```

   **Output**:
   ```
        name  age      city
   0    Alice   25  New York
   1      Bob   30    London
   2  Charlie   35     Tokyo
   ```

---

#### Reading/Writing Data

1. **Read CSV File**:

   ```python
   # Example: Read a CSV file
   df = pd.read_csv("data.csv")
   print(df.head(2))  # Display first 2 rows
   ```

   **Output** (example):
   ```
      id   name  value
   0   1  Alice    100
   1   2    Bob    200
   ```

2. **Write to CSV**:

   ```python
   df.to_csv("output.csv", index=False)
   ```

---

#### Data Inspection

1. **First/Last Rows**:

   ```python
   print(df.head(2))  # First 2 rows
   print(df.tail(1))  # Last row
   ```

   **Output**:
   ```
        name  age      city
   0    Alice   25  New York
   1      Bob   30    London

        name  age   city
   2  Charlie   35  Tokyo
   ```

2. **Data Types and Missing Values**:

   ```python
   print(df.info())
   ```

   **Output**:
   ```
   <class 'pandas.core.frame.DataFrame'>
   RangeIndex: 3 entries, 0 to 2
   Data columns (total 3 columns):
    #   Column  Non-Null Count  Dtype 
   ---  ------  --------------  ----- 
   0   name    3 non-null      object
   1   age     3 non-null      int64 
   2   city    3 non-null      object
   dtypes: int64(1), object(2)
   ```

3. **Summary Statistics**:

   ```python
   print(df.describe())
   ```

   **Output**:
   ```
              age
   count   3.000000
   mean   30.000000
   std     5.000000
   min    25.000000
   25%    27.500000
   50%    30.000000
   75%    32.500000
   max    35.000000
   ```

---

#### Selection and Indexing

1. **Select Columns**:

   ```python
   print(df["name"])  # Select "name" column
   ```

   **Output**:
   ```
   0      Alice
   1        Bob
   2    Charlie
   Name: name, dtype: object
   ```

2. **Select Rows**:

   ```python
   print(df.iloc[1])  # Select row at index 1
   ```

   **Output**:
   ```
   name      Bob
   age       30
   city    London
   Name: 1, dtype: object
   ```

3. **Filter Rows**:

   ```python
   filtered = df[df["age"] > 25]
   print(filtered)
   ```

   **Output**:
   ```
        name  age    city
   1      Bob   30  London
   2  Charlie   35   Tokyo
   ```

---

#### Data Manipulation

1. **Add a Column**:

   ```python
   df["salary"] = [70000, 80000, 90000]
   print(df)
   ```

   **Output**:
   ```
        name  age      city  salary
   0    Alice   25  New York   70000
   1      Bob   30    London   80000
   2  Charlie   35     Tokyo   90000
   ```

2. **Rename Columns**:

   ```python
   df.rename(columns={"city": "location"}, inplace=True)
   print(df)
   ```

   **Output**:
   ```
        name  age  location  salary
   0    Alice   25  New York   70000
   1      Bob   30    London   80000
   2  Charlie   35     Tokyo   90000
   ```

3. **Apply a Function**:

   ```python
   df["age_plus_5"] = df["age"].apply(lambda x: x + 5)
   print(df)
   ```

   **Output**:
   ```
        name  age  location  salary  age_plus_5
   0    Alice   25  New York   70000          30
   1      Bob   30    London   80000          35
   2  Charlie   35     Tokyo   90000          40
   ```

---

#### Handling Missing Data

1. **Detect Missing Values**:

   ```python
   df_missing = pd.DataFrame({"A": [1, None, 3], "B": [None, 5, 6]})
   print(df_missing.isna())
   ```

   **Output**:
   ```
        A      B
   0  False   True
   1   True  False
   2  False  False
   ```

2. **Fill Missing Values**:

   ```python
   df_filled = df_missing.fillna(0)
   print(df_filled)
   ```

   **Output**:
   ```
      A    B
   0  1.0  0.0
   1  0.0  5.0
   2  3.0  6.0
   ```

---

#### Aggregation and Grouping

1. **GroupBy**:

   ```python
   df_group = pd.DataFrame({
       "department": ["HR", "Tech", "HR", "Tech"],
       "salary": [50000, 80000, 60000, 90000]
   })
   grouped = df_group.groupby("department").mean()
   print(grouped)
   ```

   **Output**:
   ```
             salary
   department       
   HR        55000.0
   Tech      85000.0
   ```

2. **Aggregate Functions**:

   ```python
   print(df_group["salary"].sum())  # Total salary: 280000
   ```

---

#### Merging/Joining DataFrames

1. **Concatenate**:

   ```python
   df1 = pd.DataFrame({"A": [1, 2], "B": [3, 4]})
   df2 = pd.DataFrame({"A": [5, 6], "B": [7, 8]})
   combined = pd.concat([df1, df2], ignore_index=True)
   print(combined)
   ```

   **Output**:
   ```
      A  B
   0  1  3
   1  2  4
   2  5  7
   3  6  8
   ```

2. **Merge**:

   ```python
   left = pd.DataFrame({"key": ["A", "B"], "value": [1, 2]})
   right = pd.DataFrame({"key": ["B", "C"], "value": [3, 4]})
   merged = pd.merge(left, right, on="key", how="left")
   print(merged)
   ```

   **Output**:
   ```
     key  value_x  value_y
   0   A        1      NaN
   1   B        2      3.0
   ```

---

#### Time Series

1. **Date Range**:

   ```python
   dates = pd.date_range("2023-01-01", periods=3)
   df_dates = pd.DataFrame({"date": dates, "sales": [100, 200, 300]})
   print(df_dates)
   ```

   **Output**:
   ```
          date  sales
   0 2023-01-01    100
   1 2023-01-02    200
   2 2023-01-03    300
   ```

2. **Resample Time Series**:

   ```python
   df_dates.set_index("date", inplace=True)
   monthly = df_dates.resample("M").sum()
   print(monthly)
   ```

   **Output**:
   ```
               sales
   date             
   2023-01-31    600
   ```

---

#### Plotting with Pandas

```python
df.plot(x="name", y="salary", kind="bar")
```

**Output**:  
A bar chart showing salaries for Alice, Bob, and Charlie.

---

#### Conclusion

Pandas is the backbone of data manipulation in Python. Its intuitive syntax and powerful tools for data cleaning, transformation, and analysis make it indispensable for data professionals. By mastering Pandas, you can efficiently handle real-world datasets and derive actionable insights.

---

#### Further Reading

- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Python for Data Analysis by Wes McKinney](https://www.oreilly.com/library/view/python-for-data/9781098104023/)
- [Real Python Tutorials](https://realpython.com/learning-paths/pandas-data-science/)

This concludes the detailed lecture on Pandas in Python. Happy analyzing! 📊
