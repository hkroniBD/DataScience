# **Python Programming - Lecture 2: Variables and Data Types**  

## **1. What is a Variable?**  
A **variable** is a name that stores a value. In Python, you don’t need to declare the type of a variable; Python automatically determines it.  

### **Example: Assigning Variables**
```python
name = "Alice"   # String
age = 25         # Integer
height = 5.6     # Float
is_student = True  # Boolean

print(name)
print(age)
print(height)
print(is_student)
```
**Output:**
```
Alice
25
5.6
True
```

---

## **2. Rules for Naming Variables**  
1. A variable name must start with a letter or an underscore (`_`).  
2. It **cannot** start with a number.  
3. It **can** contain letters, numbers, and underscores.  
4. It is **case-sensitive** (`age` and `Age` are different).  
5. Avoid using **Python keywords** (e.g., `print`, `if`, `else`).  

**Valid Variable Names:**
```python
my_name = "John"
_age = 30
height_in_meters = 1.75
```

**Invalid Variable Names (will cause errors):**
```python
2name = "John"    # Cannot start with a number
my-name = "John"  # Cannot contain hyphens
class = "Math"    # 'class' is a reserved keyword
```

---

## **3. Data Types in Python**  
Python supports different types of data. Here are some common ones:  

| Data Type | Example | Description |
|-----------|---------|-------------|
| **String (`str`)** | `"Hello"` | Text data enclosed in quotes |
| **Integer (`int`)** | `10, -5, 0` | Whole numbers |
| **Float (`float`)** | `3.14, -0.5` | Decimal numbers |
| **Boolean (`bool`)** | `True, False` | Represents True or False |
| **List (`list`)** | `[1, 2, 3]` | Ordered collection of items |
| **Tuple (`tuple`)** | `(4, 5, 6)` | Immutable ordered collection |
| **Dictionary (`dict`)** | `{"name": "Alice", "age": 25}` | Key-value pairs |

---

## **4. Checking Data Types**  
You can check the type of a variable using `type()`.  

### **Example:**
```python
x = "Hello"
y = 10
z = 3.14
a = True

print(type(x))  # str
print(type(y))  # int
print(type(z))  # float
print(type(a))  # bool
```
**Output:**
```
<class 'str'>
<class 'int'>
<class 'float'>
<class 'bool'>
```

---

## **5. Type Conversion (Casting)**  
Sometimes, you need to convert one data type into another.

### **Example: Converting Between Types**
```python
# Convert int to float
num = 10
num_float = float(num)
print(num_float)  # 10.0

# Convert float to int
price = 9.99
price_int = int(price)
print(price_int)  # 9

# Convert number to string
age = 25
age_str = str(age)
print(age_str)  # "25"

# Convert string to int
text = "100"
num = int(text)
print(num)  # 100
```

---

## **6. Multiple Assignments**  
You can assign multiple variables in one line.

```python
a, b, c = 5, 10, 15
print(a, b, c)  # 5 10 15

# Assigning the same value to multiple variables
x = y = z = 50
print(x, y, z)  # 50 50 50
```

---

## **7. User Input**  
Python allows users to input values using the `input()` function.

### **Example: Taking User Input**
```python
name = input("Enter your name: ")
age = input("Enter your age: ")

print("Hello, " + name + "! You are " + age + " years old.")
```
**Example Output:**
```
Enter your name: Alice
Enter your age: 25
Hello, Alice! You are 25 years old.
```

**Note:** `input()` always returns a string. If you need a number, convert it using `int()` or `float()`.
```python
age = int(input("Enter your age: "))
print(age + 5)  # Adds 5 to the entered age
```

---

### **Conclusion**  
- You learned about variables and their naming rules.  
- You explored different data types and how to check them.  
- You practiced type conversion.  
- You learned about user input in Python.  

---

### **Next Lecture: Operators in Python**  
