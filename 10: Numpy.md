### **Lecture 10: Python NumPy**

---

### **1. Introduction to NumPy**

**NumPy** (Numerical Python) is a powerful library in Python used for numerical and matrix operations. It provides support for large, multi-dimensional arrays and matrices, along with a collection of mathematical functions to operate on these arrays.

NumPy is the foundation of numerical computing in Python, and many other scientific computing libraries (like Pandas, SciPy, etc.) depend on it.

---

### **2. NumPy | `ndarray`**

The **`ndarray`** (N-dimensional array) is the core data structure in NumPy. It is a grid of values, all of the same type, indexed by a tuple of non-negative integers.

#### **2.1 Key Characteristics**:
- **Homogeneous**: All elements of an array are of the same type.
- **Multidimensional**: Supports arrays of any number of dimensions.
- **Efficient**: Optimized for fast computation and memory usage.

#### **2.2 Creating a `ndarray`**:
```python
import numpy as np

# 1D array
arr = np.array([1, 2, 3, 4])
print(arr)

# 2D array (Matrix)
matrix = np.array([[1, 2], [3, 4]])
print(matrix)

# 3D array
tensor = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
print(tensor)
```

---

### **3. NumPy | Array Creation**

NumPy offers several functions to create arrays:

- **`np.array()`**: Creates arrays from lists or tuples.
- **`np.zeros()`**: Creates an array filled with zeros.
- **`np.ones()`**: Creates an array filled with ones.
- **`np.arange()`**: Creates an array with a range of values.
- **`np.linspace()`**: Creates an array with linearly spaced values.

#### **3.1 Examples**:
```python
arr1 = np.zeros((2, 3))  # 2x3 array filled with zeros
arr2 = np.ones((3, 2))  # 3x2 array filled with ones
arr3 = np.arange(10)  # Array with values from 0 to 9
arr4 = np.linspace(0, 10, 5)  # 5 equally spaced values between 0 and 10
```

---

### **4. NumPy | Data Type Objects (`dtype`)**

The **`dtype`** (data type) object in NumPy specifies the type of elements in the array. NumPy supports various data types such as `int`, `float`, `complex`, `bool`, `str`, etc.

#### **4.1 Example**:
```python
arr = np.array([1, 2, 3, 4], dtype=np.float64)  # Float type array
print(arr.dtype)  # Output: float64
```

You can explicitly define the data type while creating the array or use `.astype()` to convert the data type.

#### **4.2 Changing Data Type**:
```python
arr = np.array([1, 2, 3, 4])
arr = arr.astype(np.float32)
print(arr.dtype)  # Output: float32
```

---

### **5. NumPy | Indexing**

Indexing in NumPy allows access to elements of arrays and sub-arrays using integer indices or slices.

#### **5.1 Example**:
```python
arr = np.array([10, 20, 30, 40])
print(arr[0])  # Output: 10
print(arr[-1])  # Output: 40 (last element)
```

For **2D arrays**, indexing can be done with two indices, like `array[row, column]`:
```python
matrix = np.array([[1, 2], [3, 4], [5, 6]])
print(matrix[1, 0])  # Output: 3
```

---

### **6. NumPy | Basic Slicing and Advanced Indexing**

- **Slicing**: Allows you to extract a part of the array.
  - Syntax: `array[start:stop:step]`

#### **6.1 Example of Basic Slicing**:
```python
arr = np.array([1, 2, 3, 4, 5])
print(arr[1:4])  # Output: [2 3 4]

# 2D slicing
matrix = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(matrix[1:3, 1:3])  # Output: [[5 6] [8 9]]
```

- **Advanced Indexing**: Allows using lists or arrays of indices.
```python
arr = np.array([10, 20, 30, 40, 50])
print(arr[[0, 2, 4]])  # Output: [10 30 50]
```

---

### **7. NumPy | Iterating Over Array**

You can iterate over elements of a NumPy array using regular Python loops or vectorized operations.

#### **7.1 Example**:
```python
arr = np.array([1, 2, 3, 4, 5])
for element in arr:
    print(element)
```

For multi-dimensional arrays, you can use `nditer` to iterate over the array efficiently:
```python
matrix = np.array([[1, 2], [3, 4]])
for x in np.nditer(matrix):
    print(x)
```

---

### **8. NumPy | Binary Operations**

NumPy supports a wide range of **binary operations** like addition, subtraction, multiplication, division, etc., for arrays of the same shape.

#### **8.1 Example**:
```python
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
result = arr1 + arr2  # Element-wise addition
print(result)  # Output: [5 7 9]

# Element-wise multiplication
result = arr1 * arr2
print(result)  # Output: [4 10 18]
```

---

### **9. NumPy | Linear Algebra**

NumPy provides functions for performing linear algebra operations such as matrix multiplication, dot products, and solving linear equations.

#### **9.1 Example**:
```python
A = np.array([[1, 2], [3, 4]])
B = np.array([[5, 6], [7, 8]])

# Matrix multiplication
result = np.dot(A, B)
print(result)

# Determinant of a matrix
det = np.linalg.det(A)
print(det)
```

---

### **10. NumPy | Sorting, Searching, and Counting**

NumPy offers a range of functions for sorting, searching, and counting elements in arrays.

- **`np.sort()`**: Sorts an array.
- **`np.searchsorted()`**: Finds indices where elements should be inserted.
- **`np.count_nonzero()`**: Counts the number of non-zero elements.

#### **10.1 Examples**:

```python
arr = np.array([5, 2, 9, 1, 5, 6])

# Sorting array
sorted_arr = np.sort(arr)
print(sorted_arr)  # Output: [1 2 5 5 6 9]

# Searching for an element
index = np.searchsorted(sorted_arr, 5)
print(index)  # Output: 3

# Counting non-zero elements
non_zero_count = np.count_nonzero(arr)
print(non_zero_count)  # Output: 6
```

---

### **Quiz**

1. **What is the default data type when you create a NumPy array from a list of integers?**

    a) `float64`  
    b) `int32`  
    c) `int64`  
    d) `str`

2. **How would you create a 5x5 array of zeros using NumPy?**

    a) `np.zeros(5, 5)`  
    b) `np.zeros((5, 5))`  
    c) `np.array([[0] * 5] * 5)`  
    d) `np.array(zeros(5, 5))`

3. **Which function would you use to find the indices of elements in a sorted array where a new element should be inserted?**

    a) `np.sort()`  
    b) `np.searchsorted()`  
    c) `np.insert()`  
    d) `np.count_nonzero()`

4. **What is the result of `np.array([1, 2, 3]) + np.array([4, 5, 6])`?**

    a) `[1, 2, 3, 4, 5, 6]`  
    b) `[5, 7, 9]`  
    c) `[4, 5, 6]`  
    d) `None of the above`

5. **How do you perform matrix multiplication in NumPy?**

    a) `np.multiply()`  
    b) `np.dot()`  
    c) `np.matmul()`  
    d) `np.sum()`

---

### **Answer Key**

1. **b) `int32`**
2. **b) `np.zeros((5, 5))`**
3. **b) `np.searchsorted()`**
4. **b) `[5, 7, 9]`**
5. **b) `np.dot()`**

---

### **Summary**

In this lecture, we covered:
1. **NumPy `ndarray`**: The primary data structure in NumPy.
2. **Array Creation**: Different ways to create arrays in NumPy.
3. **Data Types in NumPy**: Understanding the `dtype` and how to work with different data types.
4. **Indexing & Slicing**: Basic and advanced techniques for accessing elements in arrays.
5. **Iterating Over Arrays**: How to iterate over arrays in both 1D and multidimensional forms.
6. **Binary Operations**: Performing element-wise operations on arrays.
7. **Linear Algebra**: Using NumPy for matrix operations and linear algebra calculations.
8. **Sorting, Searching, and Counting**: Useful functions for array manipulation.

NumPy is an essential tool for efficient computation in Python, especially when dealing with large datasets or performing mathematical operations.
