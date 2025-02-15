### **Lecture 6: Python Loops and Control Statements**

---

### **1. Python Loops**
In Python, loops allow you to execute a block of code multiple times. There are two primary types of loops: **for loops** and **while loops**.

#### **1.1 For Loop**
The `for` loop is used for iterating over a sequence (such as a list, tuple, dictionary, string, or range) and executing a block of code for each item in the sequence.

- **Syntax**:
  ```python
  for item in sequence:
      # Execute block of code
  ```

- **Example**:
  ```python
  fruits = ["apple", "banana", "cherry"]
  for fruit in fruits:
      print(fruit)
  ```

  **Output**:
  ```
  apple
  banana
  cherry
  ```

#### **1.2 While Loop**
The `while` loop runs as long as a specified condition is `True`. The condition is checked before each iteration.

- **Syntax**:
  ```python
  while condition:
      # Execute block of code
  ```

- **Example**:
  ```python
  count = 0
  while count < 5:
      print(count)
      count += 1
  ```

  **Output**:
  ```
  0
  1
  2
  3
  4
  ```

---

### **2. Control Statements in Python**
Control statements are used to alter the flow of execution in loops and functions. They allow us to skip iterations, break out of loops, or do nothing.

#### **2.1 `break` Statement**
The `break` statement is used to exit the loop prematurely, regardless of the loop condition.

- **Example**:
  ```python
  for i in range(10):
      if i == 5:
          break
      print(i)
  ```

  **Output**:
  ```
  0
  1
  2
  3
  4
  ```

  The loop breaks when `i == 5`.

#### **2.2 `continue` Statement**
The `continue` statement skips the current iteration and proceeds to the next iteration of the loop.

- **Example**:
  ```python
  for i in range(5):
      if i == 2:
          continue
      print(i)
  ```

  **Output**:
  ```
  0
  1
  3
  4
  ```

  The number `2` is skipped in the output.

#### **2.3 `pass` Statement**
The `pass` statement is a placeholder that does nothing. It's useful when the syntax requires a statement but you don't want to execute anything.

- **Example**:
  ```python
  for i in range(3):
      if i == 1:
          pass  # Does nothing when i == 1
      else:
          print(i)
  ```

  **Output**:
  ```
  0
  2
  ```

  The `pass` statement is used when `i == 1`, so the loop does nothing for that iteration.

---

### **3. Looping Techniques in Python**
There are several ways to iterate through a sequence in Python, offering flexibility to the programmer.

#### **3.1 Iterating Through Lists, Tuples, and Strings**
You can use a `for` loop to iterate through any iterable (e.g., lists, tuples, and strings).

- **Example (List)**:
  ```python
  my_list = [1, 2, 3]
  for item in my_list:
      print(item)
  ```

- **Example (String)**:
  ```python
  word = "hello"
  for letter in word:
      print(letter)
  ```

#### **3.2 Iterating Through Dictionaries**
When looping through a dictionary, you can use the `.items()` method to iterate through key-value pairs.

- **Example**:
  ```python
  my_dict = {"a": 1, "b": 2, "c": 3}
  for key, value in my_dict.items():
      print(f"{key}: {value}")
  ```

  **Output**:
  ```
  a: 1
  b: 2
  c: 3
  ```

#### **3.3 Using `else` in Loops**
You can use an `else` block in loops that runs if the loop completes normally (i.e., without a `break` statement).

- **Example**:
  ```python
  for i in range(3):
      print(i)
  else:
      print("Loop finished")
  ```

  **Output**:
  ```
  0
  1
  2
  Loop finished
  ```

---

### **4. `range()` vs `xrange()` in Python**
The `range()` function is used to generate a sequence of numbers, which can be iterated over in loops.

- **`range()` in Python 2 vs 3**:
  - In **Python 2**, `range()` returns a list, and `xrange()` returns an iterator.
  - In **Python 3**, `range()` returns an iterator, and `xrange()` is no longer available.

- **Example (Python 3)**:
  ```python
  for i in range(5):
      print(i)
  ```

  **Output**:
  ```
  0
  1
  2
  3
  4
  ```

---

### **5. Chaining Comparison in Python**
Python allows you to chain comparison operators to evaluate multiple conditions in one statement. This is called "chaining comparison".

#### **5.1 Syntax**:
```python
x < y <= z
```

This is equivalent to:
```python
x < y and y <= z
```

- **Example**:
  ```python
  x = 5
  y = 10
  z = 15
  print(x < y <= z)  # Output: True
  ```

Chaining comparisons is more readable and efficient in Python.

---

### **Quiz**

1. **Basic Looping**: Write a `for` loop to print all the even numbers from 0 to 20.
   
2. **Control Statement**: Write a program that prints numbers from 1 to 10 but skips the number 7 using the `continue` statement.

3. **Using `break`**: Create a `while` loop that prints numbers from 1 to 10 and stops when it reaches 5.

4. **Chaining Comparison**: Check if the number `10` lies between `5` and `15` using a chained comparison.

---

### **Answer Key**

#### **1. Basic Looping**
```python
for i in range(0, 21, 2):
    print(i)
```

#### **2. Control Statement**
```python
for i in range(1, 11):
    if i == 7:
        continue
    print(i)
```

#### **3. Using `break`**
```python
i = 1
while i <= 10:
    if i == 5:
        break
    print(i)
    i += 1
```

#### **4. Chaining Comparison**
```python
x = 10
if 5 < x <= 15:
    print("10 is between 5 and 15")
```

---

### **Summary**
This lecture covered:
1. The `for` and `while` loops in Python.
2. Control statements (`break`, `continue`, `pass`) to control the flow of execution in loops.
3. Looping techniques for iterating through lists, strings, dictionaries, and using `else` in loops.
4. Understanding the difference between `range()` and `xrange()` in Python 2 and Python 3.
5. Chaining comparisons to evaluate multiple conditions concisely.

This is essential knowledge for effective iteration and flow control in Python.
