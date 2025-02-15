## **Lecture 4: Variables, Expressions, Conditional Statements, and Functions in Python**

---

### **1. Variables in Python**
- **Definition**: A variable is a name that refers to a value stored in memory. It acts as a container for data.

- **Declaring Variables**: In Python, variables are dynamically typed. You don’t need to specify a type when declaring a variable.

  Example:
  ```python
  x = 10          # integer
  y = 5.5         # floating point
  name = "Alice"   # string
  is_active = True # boolean
  ```

- **Types of Variables**:
  - **Integer**: Whole numbers.
  - **Float**: Numbers with decimals.
  - **String**: Text data enclosed in single or double quotes.
  - **Boolean**: True or False.

- **Variable Re-assignment**: Variables can be reassigned to different values during the program's execution.
  
  Example:
  ```python
  x = 10
  x = "Hello"   # Now x is a string
  ```

---

### **2. Expressions and Operators**
An **expression** is a combination of variables, constants, operators, and function calls that are evaluated to produce a value.

- **Arithmetic Operators**: Used for performing basic arithmetic operations.
  ```python
  x = 10 + 5  # Addition
  y = 10 - 5  # Subtraction
  z = 10 * 5  # Multiplication
  a = 10 / 5  # Division (returns float)
  b = 10 // 3 # Floor Division (returns integer)
  c = 10 % 3  # Modulo (remainder)
  d = 10 ** 3 # Exponentiation
  ```

- **Comparison Operators**: Used to compare values.
  ```python
  10 == 10  # Equal
  10 != 5   # Not equal
  10 < 5    # Less than
  10 > 5    # Greater than
  10 <= 10  # Less than or equal
  10 >= 5   # Greater than or equal
  ```

- **Logical Operators**: Used for logical operations.
  ```python
  True and False   # Returns False
  True or False    # Returns True
  not True         # Returns False
  ```

---

### **3. Conditional Statements**
Conditional statements allow you to execute code only if a certain condition is true.

- **`if` Statement**: Evaluates an expression and runs the associated block of code if true.
  ```python
  age = 18
  if age >= 18:
      print("Adult")
  ```

- **`elif` Statement**: Used to check additional conditions if the initial `if` is false.
  ```python
  age = 15
  if age >= 18:
      print("Adult")
  elif age >= 13:
      print("Teenager")
  else:
      print("Child")
  ```

- **`else` Statement**: Executes a block of code if none of the `if` or `elif` conditions are true.

  ```python
  age = 5
  if age >= 18:
      print("Adult")
  else:
      print("Not an Adult")
  ```

- **Ternary Conditional (Shortened form of if-else)**:
  ```python
  age = 18
  result = "Adult" if age >= 18 else "Minor"
  ```

---

### **4. Functions in Python**
A function is a block of code that only runs when it is called.

- **Defining Functions**: Functions are defined using the `def` keyword.
  
  Example:
  ```python
  def greet(name):
      return f"Hello, {name}!"
  
  print(greet("Alice"))  # Output: Hello, Alice!
  ```

- **Maximum Possible Value of an Integer**: Python allows arbitrarily large integers. The integer type (`int`) in Python does not have a fixed limit. The memory limit is the only constraint.
  
  Example:
  ```python
  large_number = 10**100
  print(large_number)  # A very large number
  ```

- **Return Statement**: Functions can return values using the `return` keyword.
  
  Example:
  ```python
  def add(x, y):
      return x + y
  ```

---

### **5. Scope of Variables in Python**
The **scope** of a variable determines where it is accessible in the program.

- **Local Scope**: Variables declared inside a function are local to that function.
  
  Example:
  ```python
  def my_function():
      x = 10  # Local variable
      print(x)
  my_function()  # Output: 10
  ```

- **Global Scope**: Variables declared outside all functions are global and can be accessed by any part of the code.
  
  Example:
  ```python
  x = 10  # Global variable
  
  def print_value():
      print(x)  # Accessing global variable
  
  print_value()  # Output: 10
  ```

- **`global` Keyword**: Used to modify a global variable inside a function.

  Example:
  ```python
  x = 10
  
  def modify_global():
      global x
      x = 20  # Modify global variable
  
  modify_global()
  print(x)  # Output: 20
  ```

- **`nonlocal` Keyword**: Used to modify variables in the nearest enclosing scope (but not global).

  Example:
  ```python
  def outer():
      x = 10
      
      def inner():
          nonlocal x
          x = 20  # Modify variable in outer function's scope
          
      inner()
      print(x)  # Output: 20
  outer()
  ```

---

### **6. Packing and Unpacking Arguments**
In Python, we can pass a variable number of arguments to a function.

- **Packing Arguments with `*args`**:
  The `*args` syntax allows you to pass a variable number of positional arguments to a function.
  
  Example:
  ```python
  def sum_numbers(*args):
      return sum(args)
  
  print(sum_numbers(1, 2, 3, 4))  # Output: 10
  ```

- **Unpacking Arguments**: Use `*` to unpack arguments when calling a function.
  
  Example:
  ```python
  def greet(name, age):
      print(f"Hello {name}, you are {age} years old")
  
  details = ("Alice", 30)
  greet(*details)  # Unpacking tuple
  ```

- **Packing and Unpacking with `**kwargs`**: Used for passing a variable number of keyword arguments (key-value pairs).
  
  Example:
  ```python
  def display_info(**kwargs):
      for key, value in kwargs.items():
          print(f"{key}: {value}")
  
  display_info(name="Alice", age=30)
  ```

---

### **7. Type Conversion in Python**
Type conversion refers to changing the data type of a variable.

- **Implicit Type Conversion**: Python automatically converts types when needed.
  
  Example:
  ```python
  x = 5   # int
  y = 2.5 # float
  z = x + y  # Python automatically converts x to float for the addition
  ```

- **Explicit Type Conversion**: Use functions like `int()`, `float()`, `str()` to convert explicitly.
  
  Example:
  ```python
  num = "10"
  num_int = int(num)  # Convert string to integer
  ```

---

### **8. Byte Objects vs Strings**
- **Byte Objects**: A byte object represents a sequence of bytes and is immutable.
  ```python
  byte_data = b"Hello"
  ```

- **Strings**: A string is a sequence of characters (Unicode).
  
  Example:
  ```python
  text = "Hello"
  ```

- **Conversion**: You can convert between strings and bytes using `.encode()` and `.decode()`.

  Example:
  ```python
  byte_data = text.encode('utf-8')  # Convert string to byte object
  text_back = byte_data.decode('utf-8')  # Convert byte object back to string
  ```

---

### **9. Swapping Variables**
Swapping variables in Python is easy using tuple unpacking.

- **Example**:
  ```python
  a = 5
  b = 10
  a, b = b, a  # Swap values
  print(a, b)  # Output: 10 5
  ```

---

### **10. Private Variables in OOP**
In Python, private variables are indicated by double underscores (`__`), though this is more of a convention than an enforced rule.

- **Example**:
  ```python
  class MyClass:
      def __init__(self):
          self.__private_variable = 42
      
      def get_private_variable(self):
          return self.__private_variable
  
  obj = MyClass()
  print(obj.get_private_variable())  # Access private variable
  ```

---

### **11. `__name__` Special Variable**
The `__name__` variable is used to check whether a Python script is being run as the main program or being imported as a module.

- **Example**:
  ```python
  def main():
      print("This is the main function!")
  
  if __name__ == "__main__":
      main()
  ```

---

### **Assignments:**
1. **Function Exercise**: Write a function that takes two numbers and returns their maximum.
2. **Swapping Exercise**: Write a Python program that swaps two numbers without using a third variable.
3. **Private Variable Exercise**: Create a class with a private variable and write methods to get and set its value.

--- 
