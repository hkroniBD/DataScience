### Lecture on NumPy in Python

---

#### Introduction to NumPy

**NumPy** (Numerical Python) is a fundamental package for scientific computing in Python. It provides support for arrays, matrices, and many mathematical functions to operate on these data structures. NumPy is highly optimized for performance, making it an essential tool for data analysis, machine learning, and scientific research.

---

#### Key Features of NumPy

1. **Ndarray Object**: A powerful N-dimensional array object.
2. **Broadcasting**: Functions to perform operations on arrays of different shapes.
3. **Linear Algebra**: Comprehensive set of functions for linear algebra operations.
4. **Random Number Generation**: Tools for generating random numbers.
5. **Integration with Other Libraries**: Seamless integration with libraries like SciPy, Pandas, and Matplotlib.

---

#### Installation

To install NumPy, you can use pip:

```bash
pip install numpy
```

---

#### Importing NumPy

To use NumPy, you need to import it:

```python
import numpy as np
```

---

#### Creating NumPy Arrays

1. **From a List**:

   ```python
   arr = np.array([1, 2, 3, 4, 5])
   print(arr)
   ```

   **Output**:
   ```
   [1 2 3 4 5]
   ```

2. **Multi-dimensional Arrays**:

   ```python
   arr_2d = np.array([[1, 2, 3], [4, 5, 6]])
   print(arr_2d)
   ```

   **Output**:
   ```
   [[1 2 3]
    [4 5 6]]
   ```

3. **Using Built-in Functions**:

   - **Zeros**: Creates an array filled with zeros.

     ```python
     zeros_arr = np.zeros((2, 3))
     print(zeros_arr)
     ```

     **Output**:
     ```
     [[0. 0. 0.]
      [0. 0. 0.]]
     ```

   - **Ones**: Creates an array filled with ones.

     ```python
     ones_arr = np.ones((2, 3))
     print(ones_arr)
     ```

     **Output**:
     ```
     [[1. 1. 1.]
      [1. 1. 1.]]
     ```

   - **Full**: Creates an array filled with a specific value.

     ```python
     full_arr = np.full((2, 3), 7)
     print(full_arr)
     ```

     **Output**:
     ```
     [[7 7 7]
      [7 7 7]]
     ```

   - **Identity Matrix**: Creates an identity matrix.

     ```python
     identity_matrix = np.eye(3)
     print(identity_matrix)
     ```

     **Output**:
     ```
     [[1. 0. 0.]
      [0. 1. 0.]
      [0. 0. 1.]]
     ```

   - **Arange**: Creates an array with a range of values.

     ```python
     range_arr = np.arange(0, 10, 2)
     print(range_arr)
     ```

     **Output**:
     ```
     [0 2 4 6 8]
     ```

   - **Linspace**: Creates an array with evenly spaced values.

     ```python
     linspace_arr = np.linspace(0, 10, 5)
     print(linspace_arr)
     ```

     **Output**:
     ```
     [ 0.   2.5  5.   7.5 10. ]
     ```

---

#### Array Attributes

1. **Shape**: Returns the dimensions of the array.

   ```python
   print(arr_2d.shape)
   ```

   **Output**:
   ```
   (2, 3)
   ```

2. **Size**: Returns the total number of elements in the array.

   ```python
   print(arr_2d.size)
   ```

   **Output**:
   ```
   6
   ```

3. **Dtype**: Returns the data type of the array elements.

   ```python
   print(arr_2d.dtype)
   ```

   **Output**:
   ```
   int64
   ```

---

#### Array Operations

1. **Element-wise Operations**:

   ```python
   a = np.array([1, 2, 3])
   b = np.array([4, 5, 6])
   print(a + b)
   print(a - b)
   print(a * b)
   print(a / b)
   ```

   **Output**:
   ```
   [5 7 9]
   [-3 -3 -3]
   [ 4 10 18]
   [0.25 0.4  0.5 ]
   ```

2. **Dot Product**:

   ```python
   dot_product = np.dot(a, b)
   print(dot_product)
   ```

   **Output**:
   ```
   32
   ```

3. **Matrix Multiplication**:

   ```python
   mat_a = np.array([[1, 2], [3, 4]])
   mat_b = np.array([[5, 6], [7, 8]])
   mat_product = np.matmul(mat_a, mat_b)
   print(mat_product)
   ```

   **Output**:
   ```
   [[19 22]
    [43 50]]
   ```

4. **Reshaping Arrays**:

   ```python
   reshaped_arr = np.arange(6).reshape(2, 3)
   print(reshaped_arr)
   ```

   **Output**:
   ```
   [[0 1 2]
    [3 4 5]]
   ```

5. **Transpose**:

   ```python
   transposed_arr = reshaped_arr.T
   print(transposed_arr)
   ```

   **Output**:
   ```
   [[0 3]
    [1 4]
    [2 5]]
   ```

---

#### Indexing and Slicing

1. **Indexing**:

   ```python
   print(arr_2d[0, 1])
   ```

   **Output**:
   ```
   2
   ```

2. **Slicing**:

   ```python
   print(arr_2d[:, 1:3])
   ```

   **Output**:
   ```
   [[2 3]
    [5 6]]
   ```

---

#### Aggregation Functions

1. **Sum**:

   ```python
   print(np.sum(arr_2d))
   ```

   **Output**:
   ```
   21
   ```

2. **Mean**:

   ```python
   print(np.mean(arr_2d))
   ```

   **Output**:
   ```
   3.5
   ```

3. **Max**:

   ```python
   print(np.max(arr_2d))
   ```

   **Output**:
   ```
   6
   ```

4. **Min**:

   ```python
   print(np.min(arr_2d))
   ```

   **Output**:
   ```
   1
   ```

5. **Standard Deviation**:

   ```python
   print(np.std(arr_2d))
   ```

   **Output**:
   ```
   1.707825127659933
   ```

---

#### Broadcasting

Broadcasting allows NumPy to perform arithmetic operations on arrays of different shapes.

```python
a = np.array([1, 2, 3])
b = 2
print(a * b)
```

**Output**:
```
[2 4 6]
```

---

#### Linear Algebra

NumPy provides a comprehensive set of functions for linear algebra.

1. **Determinant**:

   ```python
   det = np.linalg.det(mat_a)
   print(det)
   ```

   **Output**:
   ```
   -2.0000000000000004
   ```

2. **Inverse**:

   ```python
   inv_mat = np.linalg.inv(mat_a)
   print(inv_mat)
   ```

   **Output**:
   ```
   [[-2.   1. ]
    [ 1.5 -0.5]]
   ```

3. **Eigenvalues and Eigenvectors**:

   ```python
   eigenvalues, eigenvectors = np.linalg.eig(mat_a)
   print(eigenvalues)
   print(eigenvectors)
   ```

   **Output**:
   ```
   [-0.37228132  5.37228132]
   [[-0.82456484 -0.41597356]
    [ 0.56576746 -0.90937671]]
   ```

---

#### Random Number Generation

NumPy provides functions to generate random numbers.

1. **Random Float**:

   ```python
   random_float = np.random.rand()
   print(random_float)
   ```

   **Output** (example):
   ```
   0.5488135039273248
   ```

2. **Random Integer**:

   ```python
   random_int = np.random.randint(1, 10)
   print(random_int)
   ```

   **Output** (example):
   ```
   7
   ```

3. **Random Array**:

   ```python
   random_arr = np.random.rand(2, 3)
   print(random_arr)
   ```

   **Output** (example):
   ```
   [[0.60276338 0.54488318 0.4236548 ]
    [0.64589411 0.43758721 0.891773  ]]
   ```

---

#### Conclusion

NumPy is an essential library for numerical computing in Python. Its powerful array operations, broadcasting, and linear algebra capabilities make it indispensable for scientific computing, data analysis, and machine learning. By mastering NumPy, you can significantly enhance your ability to perform complex numerical computations efficiently.

---

#### Further Reading

- [NumPy Documentation](https://numpy.org/doc/)
- [SciPy Documentation](https://docs.scipy.org/doc/scipy/reference/)
- [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/)

This concludes the detailed lecture on NumPy in Python. Happy coding! 🚀
