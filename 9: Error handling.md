### **Lecture 9: Exception Handling in Python**

---

### **1. Exception Handling in Python**

**Exception handling** is a mechanism in Python that allows the program to handle runtime errors gracefully. Instead of crashing the program, Python allows you to handle errors using `try`, `except`, and other keywords, ensuring that the program continues execution or performs some corrective action.

---

### **2. User-Defined Exception**

Python allows us to create custom exceptions by inheriting from the base `Exception` class. This is useful when we want to raise specific error messages for our own application logic.

#### **2.1 Creating a Custom Exception**:
- **Syntax**:
  ```python
  class CustomError(Exception):
      def __init__(self, message):
          self.message = message
          super().__init__(self.message)
  ```

- **Example**:
  ```python
  class NegativeValueError(Exception):
      def __init__(self, message="Value cannot be negative"):
          self.message = message
          super().__init__(self.message)

  def check_value(value):
      if value < 0:
          raise NegativeValueError("Negative values are not allowed!")
      else:
          print("Value is positive.")

  try:
      check_value(-5)
  except NegativeValueError as e:
      print(f"Error: {e}")
  ```

In this example, we defined a custom exception `NegativeValueError`, which is raised if a negative value is passed to the `check_value` function.

---

### **3. Built-in Exceptions**

Python provides several built-in exceptions that are raised for common error scenarios. Some of the common built-in exceptions include:

- **`IndexError`**: Raised when trying to access an index in a list that does not exist.
- **`ValueError`**: Raised when a function receives an argument of the right type but an inappropriate value.
- **`TypeError`**: Raised when an operation or function is applied to an object of inappropriate type.
- **`ZeroDivisionError`**: Raised when dividing a number by zero.
- **`KeyError`**: Raised when a dictionary key is not found.
  
#### **3.1 Example**:

```python
try:
    x = [1, 2, 3]
    print(x[5])
except IndexError as e:
    print(f"IndexError: {e}")
```

In this example, the code attempts to access an index that does not exist, raising an `IndexError`.

---

### **4. Cleanup Action: `finally` Block**

The **`finally` block** is always executed, no matter what, whether or not an exception occurs. It is typically used for clean-up actions, such as closing files or releasing resources.

#### **4.1 Syntax**:
```python
try:
    # Code that may raise an exception
except SomeException as e:
    # Handle exception
finally:
    # Code that always runs (cleanup)
```

#### **4.2 Example**:
```python
try:
    file = open("example.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found!")
finally:
    print("Closing the file.")
    file.close()
```

In this example, even if an exception is raised (like `FileNotFoundError`), the `finally` block will execute to ensure the file is closed.

---

### **5. NZEC Error (Non-Zero Exit Code)**

**NZEC (Non-Zero Exit Code)** is a general runtime error. In Python, an NZEC error can occur when a program exits with a non-zero exit code, often due to an uncaught exception or unhandled runtime errors.

#### **5.1 Common Causes of NZEC**:
- Unhandled exceptions.
- Memory overflow or segmentation faults (in C extensions).
- Input issues in competitive programming platforms.
  
#### **5.2 Example**:
```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ZeroDivisionError:
    print("Cannot divide by zero.")
except ValueError:
    print("Invalid input. Please enter an integer.")
```

If the user inputs a non-integer value or 0, an exception will be caught, and the program will not crash.

---

### **6. `try` and `except` in Python**

The `try` block is used to write code that may raise exceptions, and the `except` block is used to handle the exception.

#### **6.1 Syntax**:
```python
try:
    # Code that might raise an exception
except SomeException:
    # Code to handle exception
else:
    # Code to run if no exception occurs
finally:
    # Code that always runs
```

#### **6.2 Example**:
```python
try:
    number = int(input("Enter a number: "))
    result = 10 / number
except ZeroDivisionError:
    print("Error: Cannot divide by zero.")
except ValueError:
    print("Error: Invalid input. Please enter a number.")
else:
    print(f"Result is: {result}")
finally:
    print("Execution finished.")
```

In this example:
- If an exception is raised (like `ZeroDivisionError` or `ValueError`), the corresponding `except` block is executed.
- If no exception occurs, the `else` block runs.
- The `finally` block always runs, regardless of whether an exception occurs.

---

### **7. Assignment**

1. **User-Defined Exception**: Create a user-defined exception `NegativeAgeError` for an age input function. If a negative age is entered, raise the exception with an appropriate message.

2. **Built-in Exception**: Write a Python program to handle `KeyError` when accessing a non-existing key in a dictionary. The program should print an appropriate error message.

3. **Exception Handling with `finally`**: Write a Python program that opens a file, reads its content, and ensures the file is always closed, whether an exception is raised or not.

4. **NZEC Error**: Handle a situation where a user might input a non-integer value. Implement a `try-except` block that ensures the program handles invalid input gracefully.

---

### **Answer Key**

#### **1. User-Defined Exception**:

```python
class NegativeAgeError(Exception):
    def __init__(self, message="Age cannot be negative"):
        self.message = message
        super().__init__(self.message)

def check_age(age):
    if age < 0:
        raise NegativeAgeError("Age cannot be negative!")
    else:
        print("Valid age.")

try:
    check_age(-5)
except NegativeAgeError as e:
    print(f"Error: {e}")
```

#### **2. Built-in Exception**:

```python
person = {"name": "John", "age": 30}
try:
    print(person["address"])
except KeyError as e:
    print(f"KeyError: {e}")
```

#### **3. Exception Handling with `finally`**:

```python
try:
    file = open("test.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found!")
finally:
    print("Closing the file.")
    file.close()
```

#### **4. NZEC Error**:

```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ValueError:
    print("Invalid input. Please enter an integer.")
except ZeroDivisionError:
    print("Cannot divide by zero.")
finally:
    print("Execution finished.")
```

---

### **Summary**

In this lecture, we covered:
1. **User-Defined Exceptions**: Creating custom exceptions for specific error handling.
2. **Built-in Exceptions**: Common Python exceptions such as `IndexError`, `ValueError`, and `KeyError`.
3. **Cleanup Action**: Using the `finally` block to ensure cleanup actions.
4. **NZEC Error**: Understanding non-zero exit codes and handling common runtime errors.
5. **`try` and `except`**: Catching and handling exceptions to ensure the program runs smoothly without crashing.

Proper exception handling is essential for writing robust, error-resistant code, especially in complex applications or in scenarios with unpredictable user inputs.
