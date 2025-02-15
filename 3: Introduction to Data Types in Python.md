**Lecture 3: Introduction to Data Types in Python**

**Session Duration: 3 Hours**

---

## **1. Introduction to Data Types in Python**
### **What are Data Types?**
Data types define the type of value a variable can hold in Python. Python is a dynamically typed language, meaning variables do not need explicit type declarations.

### **Importance of Data Types:**
- Helps in memory allocation and operations.
- Defines the behavior of data manipulation.
- Essential for data science and machine learning tasks.

---

## **2. Strings in Python**
### **Definition:**
A string is a sequence of characters enclosed in single (`'`), double (`"`), or triple (`''' """`) quotes.

### **Creating Strings:**
```python
string1 = 'Hello, World!'
string2 = "Python Programming"
string3 = '''Multi-line
String Example'''
```

### **Common String Operations:**
| Operation | Example |
|-----------|---------|
| Concatenation | `"Hello" + " World"` |
| Repetition | `"Hello" * 3` |
| Slicing | `string1[0:5]` |
| Length | `len(string1)` |
| Uppercase | `string1.upper()` |
| Lowercase | `string1.lower()` |
| Split | `string1.split() ` |

---

## **3. Lists in Python**
### **Definition:**
A list is a mutable, ordered collection of elements.

### **Creating Lists:**
```python
my_list = [1, 2, 3, "Python", 4.5]
```

### **List Operations:**
| Operation | Example |
|-----------|---------|
| Accessing Elements | `my_list[0]` |
| Appending | `my_list.append(6)` |
| Removing | `my_list.remove(3)` |
| Slicing | `my_list[1:4]` |
| Sorting | `my_list.sort()` |

---

## **4. Tuples in Python**
### **Definition:**
A tuple is an immutable, ordered collection of elements.

### **Creating Tuples:**
```python
tuple1 = (1, 2, 3, "Python")
```

### **Tuple Operations:**
| Operation | Example |
|-----------|---------|
| Accessing Elements | `tuple1[0]` |
| Slicing | `tuple1[1:3]` |
| Length | `len(tuple1)` |

---

## **5. Sets in Python**
### **Definition:**
A set is an unordered collection of unique elements.

### **Creating Sets:**
```python
my_set = {1, 2, 3, 4, 5}
```

### **Set Operations:**
| Operation | Example |
|-----------|---------|
| Adding Elements | `my_set.add(6)` |
| Removing Elements | `my_set.remove(3)` |
| Union | `set1 | set2` |
| Intersection | `set1 & set2` |
| Difference | `set1 - set2` |

---

## **6. Dictionaries in Python**
### **Definition:**
A dictionary is an unordered collection of key-value pairs.

### **Creating Dictionaries:**
```python
my_dict = {"name": "Alice", "age": 25, "city": "New York"}
```

### **Dictionary Operations:**
| Operation | Example |
|-----------|---------|
| Accessing Values | `my_dict["name"]` |
| Adding Elements | `my_dict["country"] = "USA"` |
| Removing Elements | `del my_dict["age"]` |
| Keys | `my_dict.keys()` |
| Values | `my_dict.values()` |

---

## **7. Arrays in Python**
### **Definition:**
An array is a data structure that stores multiple values of the same type.

### **Creating Arrays using NumPy:**
```python
import numpy as np
my_array = np.array([1, 2, 3, 4, 5])
```

### **Array Operations:**
| Operation | Example |
|-----------|---------|
| Accessing Elements | `my_array[0]` |
| Reshaping | `my_array.reshape(2, 3)` |
| Finding Shape | `my_array.shape` |

---

## **8. Assignment & Quiz**
1. Create a Python program to demonstrate string concatenation and slicing.
2. Implement a Python program to perform various operations on lists.
3. Write a Python script to create and manipulate tuples.
4. Implement set operations (union, intersection, difference) using Python.
5. Create a dictionary and demonstrate key-value access and updates.
6. Implement a NumPy array and perform basic operations.

---

This concludes the session. Happy Coding!

---

