
## **Lecture 5: File Handling, Exception Handling, and Working with Libraries**

### **1. File Handling in Python**

File handling is essential for reading and writing data to files. Python makes it easy to work with files using built-in functions.

#### **Opening a File**

You can open a file using the `open()` function. The syntax is:
```python
file = open('filename.txt', 'mode')
```
**Modes**:
- `'r'`: Read (default mode, opens the file for reading)
- `'w'`: Write (creates a new file or overwrites an existing one)
- `'a'`: Append (opens the file for writing, appending data at the end)
- `'rb'`, `'wb'`: Read and write in binary mode

Example:
```python
file = open('example.txt', 'r')  # Open file for reading
```

#### **Reading from a File**

Once the file is opened, you can read its contents using methods like `.read()`, `.readline()`, or `.readlines()`.

- **`.read()`**: Reads the entire file.
```python
content = file.read()
print(content)
```

- **`.readline()`**: Reads one line from the file.
```python
line = file.readline()
print(line)
```

- **`.readlines()`**: Reads all lines and returns a list of lines.
```python
lines = file.readlines()
print(lines)
```

#### **Writing to a File**

You can write data to a file by using the `'w'` or `'a'` mode.

- **`.write()`**: Writes a string to the file.
```python
file = open('output.txt', 'w')
file.write("Hello, Python!")
```

- **`.writelines()`**: Writes a list of strings to a file.
```python
lines = ["Line 1\n", "Line 2\n", "Line 3\n"]
file.writelines(lines)
```

#### **Closing the File**

It's important to close a file after completing the operations to free up resources.
```python
file.close()
```

You can also use the `with` statement for automatic closing:
```python
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
# No need to manually close the file
```

#### **Exercises on File Handling:**
1. Write a program that creates a new file and writes some text into it.
2. Read the contents of an existing file and print the contents line by line.
3. Append new content to an existing file and display the result.

---

### **2. Exception Handling in Python**

**Exceptions** are errors that occur during program execution. Python provides mechanisms to catch and handle these errors gracefully.

#### **Try-Except Block**

The `try` block lets you test a block of code for errors. The `except` block allows you to handle the error.

```python
try:
    x = 1 / 0  # Division by zero error
except ZeroDivisionError as e:
    print("Error:", e)  # Handling the specific error
```

#### **Multiple Except Blocks**

You can handle different types of exceptions using multiple `except` blocks.

```python
try:
    number = int(input("Enter a number: "))
except ValueError:
    print("Oops! That was not a valid number.")
except ZeroDivisionError:
    print("Cannot divide by zero.")
```

#### **Else and Finally**

- **`else`**: If no exception occurs, the code inside the `else` block will run.
- **`finally`**: This block always executes, regardless of whether an exception occurred or not.

```python
try:
    result = 10 / 2
except ZeroDivisionError:
    print("Cannot divide by zero.")
else:
    print("Division successful:", result)
finally:
    print("Execution complete.")
```

#### **Custom Exceptions**

You can also define your own exceptions by creating a class that inherits from `Exception`.

```python
class MyCustomError(Exception):
    pass

try:
    raise MyCustomError("Something went wrong!")
except MyCustomError as e:
    print(e)
```

#### **Exercises on Exception Handling:**
1. Write a program that asks the user for a number and performs division. Handle invalid input and division by zero errors.
2. Write a program that reads from a file, and handle the case where the file does not exist.
3. Write a custom exception class to handle a specific error and demonstrate its usage.

---

### **3. Working with Libraries in Python**

Python has a large collection of built-in libraries that simplify various tasks. You can import and use these libraries in your programs.

#### **Importing Libraries**

To use a library, you need to import it using the `import` keyword.

```python
import math
print(math.sqrt(16))  # Output: 4.0
```

- **`import <library>`**: Imports the whole library.
- **`from <library> import <function>`**: Imports specific functions or classes from a library.
```python
from math import sqrt
print(sqrt(25))  # Output: 5.0
```

#### **Common Python Libraries**
- **math**: Provides mathematical functions (e.g., `sqrt()`, `pow()`, `sin()`, `cos()`).
- **random**: For generating random numbers.
```python
import random
print(random.randint(1, 100))  # Generates a random number between 1 and 100
```
- **datetime**: For working with dates and times.
```python
import datetime
now = datetime.datetime.now()
print(now)  # Prints current date and time
```
- **os**: For interacting with the operating system.
```python
import os
print(os.getcwd())  # Prints the current working directory
```

#### **Installing External Libraries**

You can install external libraries using `pip` (Python's package manager). Run this in the terminal:
```
pip install library_name
```

Example:
```bash
pip install requests
```

#### **Using External Libraries**

```python
import requests

response = requests.get('https://api.github.com')
print(response.status_code)  # Output: 200 (OK)
```

#### **Exercises on Working with Libraries:**
1. Use the `random` library to generate 5 random numbers between 1 and 100.
2. Use the `datetime` library to print the current date and time.
3. Install the `requests` library and write a program that fetches data from a URL (e.g., a weather API).

---

### **4. Summary:**

- **File Handling**: Allows reading from and writing to files using functions like `open()`, `.read()`, `.write()`, and `.close()`. Always ensure to close files or use the `with` statement.
- **Exception Handling**: Provides a way to catch and handle errors using `try`, `except`, `else`, and `finally`. You can also define custom exceptions.
- **Libraries**: Python has many built-in libraries for various tasks. You can import and use them in your program, and you can also install external libraries using `pip`.

---

### **5. Additional Practice Problems:**

1. Create a program that opens a file in write mode, writes some data, then reads the content and displays it.
2. Handle a case where the user enters an invalid file name (e.g., file not found).
3. Write a program that imports the `math` library, performs some operations like square root and trigonometric functions, and prints the results.
4. Use the `os` library to get the list of files in the current directory.
