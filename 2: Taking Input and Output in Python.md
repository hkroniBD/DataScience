**Lecture Sheet: Taking Input and Output in Python**

**Session Duration: 3 Hours**

---

## **1. Taking Input in Python**
### **Why is Input Important?**
- Allows users to interact with programs dynamically.
- Essential for data-driven applications and automation.
- Used in competitive programming and real-world applications.

---

## **2. Taking Input from Console in Python**
### **Basic Input Method**
- The `input()` function is used to take input as a string.
```python
name = input("Enter your name: ")
print("Hello,", name)
```
- Convert input to different types:
```python
age = int(input("Enter your age: "))
height = float(input("Enter your height in meters: "))
```

---

## **3. Taking Multiple Inputs from User in Python**
### **Using `split()` Method**
- Allows users to input multiple values at once.
```python
x, y, z = map(int, input("Enter three numbers: ").split())
print("Sum:", x + y + z)
```

---

## **4. Python Input Methods for Competitive Programming**
### **Using `sys.stdin.readline()` for Fast Input**
- Faster than `input()`, especially for large input sets.
```python
import sys
data = sys.stdin.readline().strip()
print("You entered:", data)
```

---

## **5. Vulnerability in `input()` Function – Python 2.x**
- In Python 2.x, `input()` evaluates input as a Python expression, leading to security risks.
- `raw_input()` was used instead in Python 2.
- In Python 3.x, `input()` is safe as it always returns a string.

---

## **6. Python | Output using `print()` Function**
### **Basic Print Statement**
```python
print("Hello, World!")
```
### **Printing Variables**
```python
name = "Alice"
print("My name is", name)
```

---

## **7. How to Print Without Newline in Python?**
```python
print("Hello", end=" ")
print("World")  # Output: Hello World
```

---

## **8. Python | `end` Parameter in `print()`**
- Used to change the default newline character.
```python
print("Python", end="-")
print("Programming")  # Output: Python-Programming
```

---

## **9. Python | `sep` Parameter in `print()`**
- Used to specify a separator between values.
```python
print("Apple", "Banana", "Cherry", sep=", ")
# Output: Apple, Banana, Cherry
```

---

## **10. Python | Output Formatting**
- Using `format()`
```python
name = "Alice"
age = 25
print("My name is {} and I am {} years old".format(name, age))
```
- Using f-strings (Python 3.6+)
```python
print(f"My name is {name} and I am {age} years old")
```

---

## **11. Quiz**
1. What function is used to take input in Python?
2. How can you take multiple inputs in a single line?
3. What is the difference between `input()` in Python 2 and Python 3?
4. How can you print without a newline?
5. What does the `sep` parameter in `print()` do?

---

### **Assignment**
1. Write a Python program that takes two numbers as input and prints their sum.
2. Modify the program to take three numbers in a single input line.
3. Experiment with different `end` and `sep` parameters in `print()`.
4. Use formatted output to display user details.

---

This concludes the session. Happy Coding!

---

