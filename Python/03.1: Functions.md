**Python Lecture 3: Functions and Modules in Python**

**Duration:** 3 hours  

---

## **1. Introduction to Functions**  
Functions allow code reusability and improve readability. They help break down a program into smaller, manageable parts.

### **Defining and Calling a Function**  
```python
# Defining a function
def greet():
    print("Hello, welcome to Python!")

# Calling the function
greet()
```

### **Function with Parameters**  
```python
def greet_user(name):
    print(f"Hello, {name}!")

greet_user("Alice")
```

### **Function with Return Value**  
```python
def add(a, b):
    return a + b

result = add(5, 3)
print("Sum:", result)
```

---

## **2. Types of Functions**  
- **Built-in Functions**: `print()`, `len()`, `type()`, etc.  
- **User-defined Functions**: Functions created by the user.  
- **Lambda Functions**: Anonymous, single-expression functions.  

### **Lambda Function Example**  
```python
square = lambda x: x ** 2
print(square(5))  # Output: 25
```

---

## **3. Function Arguments and Parameters**  

### **Positional Arguments**  
```python
def subtract(a, b):
    return a - b

print(subtract(10, 3))  # Output: 7
```

### **Keyword Arguments**  
```python
def describe_person(name, age):
    print(f"{name} is {age} years old.")

describe_person(age=25, name="John")
```

### **Default Arguments**  
```python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet()  # Output: Hello, Guest!
```

### **Arbitrary Arguments (*args, **kwargs)**  
```python
def sum_numbers(*args):
    return sum(args)

print(sum_numbers(1, 2, 3, 4))  # Output: 10
```

```python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=30, city="New York")
```

---

## **4. Scope and Lifetime of Variables**  

- **Local Scope**: Variables inside a function are only accessible within that function.  
- **Global Scope**: Variables declared outside any function are accessible throughout the script.  

### **Example**  
```python
global_var = "I am global"

def test():
    local_var = "I am local"
    print(local_var)
    print(global_var)

test()
```


## **5. Practice Problems**  
### **Beginner Level**  
1. Write a function to calculate the square of a number.  
2. Write a function to greet a user by their name.  
3. Write a function that takes two numbers and returns their product.  

### **Intermediate Level**  
4. Write a function to check if a number is even or odd.  
5. Write a function to find the largest of three numbers.  

### **Advanced Level**  
6. Write a function that takes a list of numbers and returns the sum of all even numbers.  
7. Create a module containing functions for addition, subtraction, multiplication, and division, and import it into another script.  

---

## **7. Homework Assignment**  
1. Create a function that converts temperature from Celsius to Fahrenheit.  
2. Write a function that counts the number of vowels in a given string.  
3. Create a module with functions for basic mathematical operations and use it in another script.  
4. Write a function that accepts a string and returns it reversed.  
5. Write a function that checks if a given number is a palindrome.  

---

