### **Lecture 7: Functions in Python**

---

### **1. Functions in Python**

A function is a block of reusable code that is used to perform a specific task. Functions help in making the program modular and more readable. They can take parameters and return values.

#### **1.1 Defining a Function**
Functions are defined using the `def` keyword, followed by the function name and parameters.

- **Syntax**:
  ```python
  def function_name(parameter1, parameter2):
      # code block
      return value
  ```

- **Example**:
  ```python
  def add(a, b):
      return a + b

  result = add(3, 5)
  print(result)  # Output: 8
  ```

---

### **2. Class Method vs Static Method in Python (OOP)**

In Object-Oriented Programming (OOP), both **class methods** and **static methods** belong to the class itself, but they serve different purposes and have different ways of being called.

#### **2.1 Class Method**
A class method is a method that is bound to the class and not the instance. It takes `cls` (the class) as its first argument, which can be used to access or modify class-level variables. Class methods are defined using the `@classmethod` decorator.

- **Syntax**:
  ```python
  class MyClass:
      @classmethod
      def class_method(cls, args):
          # code block
  ```

- **Example**:
  ```python
  class Car:
      wheels = 4

      @classmethod
      def show_wheels(cls):
          print(f"A car has {cls.wheels} wheels.")

  Car.show_wheels()  # Output: A car has 4 wheels.
  ```

#### **2.2 Static Method**
A static method is bound to the class but does not take the instance (`self`) or the class (`cls`) as the first argument. It behaves like a regular function, but it belongs to the class's namespace. Static methods are defined using the `@staticmethod` decorator.

- **Syntax**:
  ```python
  class MyClass:
      @staticmethod
      def static_method(args):
          # code block
  ```

- **Example**:
  ```python
  class MathOperations:
      @staticmethod
      def add(x, y):
          return x + y

  print(MathOperations.add(2, 3))  # Output: 5
  ```

---

### **3. Yield Instead of Return**

In Python, the `yield` keyword is used to turn a function into a generator. A generator is a special type of iterator that generates values lazily, meaning one value at a time when requested. Unlike `return`, which exits the function completely, `yield` produces a value and "pauses" the function, allowing it to be resumed later.

#### **3.1 Yield Example**:
- **Syntax**:
  ```python
  def my_generator():
      yield value
  ```

- **Example**:
  ```python
  def count_up_to(max):
      count = 1
      while count <= max:
          yield count
          count += 1

  counter = count_up_to(3)
  for num in counter:
      print(num)
  ```

  **Output**:
  ```
  1
  2
  3
  ```

  The function `count_up_to` yields each number until `max` is reached. It produces values lazily, one at a time.

---

### **4. Return Multiple Values**

In Python, functions can return multiple values by separating the values with commas. The returned values can be captured as a tuple, list, or individual variables.

#### **4.1 Example**:
- **Syntax**:
  ```python
  def multiple_returns():
      return value1, value2
  ```

- **Example**:
  ```python
  def get_coordinates():
      return 5, 10

  x, y = get_coordinates()
  print(f"x: {x}, y: {y}")
  ```

  **Output**:
  ```
  x: 5, y: 10
  ```

  The function `get_coordinates()` returns two values, which are unpacked into `x` and `y`.

---

### **5. Partial Functions in Python**

A **partial function** is a function where some arguments are fixed (or "partially applied"), and it returns a new function that can accept the remaining arguments. This is achieved using the `functools.partial` method.

#### **5.1 Using `functools.partial`**:
- **Syntax**:
  ```python
  from functools import partial
  partial_function = partial(original_function, fixed_argument)
  ```

- **Example**:
  ```python
  from functools import partial

  def multiply(x, y):
      return x * y

  double = partial(multiply, 2)  # Fixing the first argument as 2
  print(double(5))  # Output: 10
  ```

  In the example, the `partial` function creates a new function `double`, which multiplies any input by 2.

---

### **6. First-Class Functions in Python**

In Python, functions are **first-class citizens**, meaning they can be treated like any other object. They can be assigned to variables, passed as arguments to other functions, and returned from other functions.

#### **6.1 Example**:
- **Assigning Functions to Variables**:
  ```python
  def greet(name):
      return f"Hello, {name}"

  greet_func = greet
  print(greet_func("Alice"))  # Output: Hello, Alice
  ```

- **Passing Functions as Arguments**:
  ```python
  def call_function(func, name):
      return func(name)

  print(call_function(greet, "Bob"))  # Output: Hello, Bob
  ```

---

### **7. Precision Handling in Python**

Precision handling refers to controlling the number of decimal places when working with floating-point numbers. Python offers various ways to handle precision.

#### **7.1 Using `round()`**:
The `round()` function allows rounding off to a specific number of decimal places.

- **Example**:
  ```python
  result = round(3.14159, 2)
  print(result)  # Output: 3.14
  ```

#### **7.2 Formatting Strings**:
You can also format numbers to a specific precision using string formatting.

- **Example**:
  ```python
  value = 3.14159
  formatted = f"{value:.2f}"
  print(formatted)  # Output: 3.14
  ```

---

### **8. `*args` and `**kwargs`**

In Python, `*args` and `**kwargs` are used to pass a variable number of arguments to a function.

#### **8.1 `*args`**:
`*args` is used to pass a variable number of positional arguments. It collects them into a tuple.

- **Example**:
  ```python
  def add(*args):
      return sum(args)

  print(add(1, 2, 3))  # Output: 6
  ```

#### **8.2 `**kwargs`**:
`**kwargs` is used to pass a variable number of keyword arguments. It collects them into a dictionary.

- **Example**:
  ```python
  def print_info(**kwargs):
      for key, value in kwargs.items():
          print(f"{key}: {value}")

  print_info(name="John", age=25)  # Output: name: John, age: 25
  ```

---

### **Quiz**

1. **Class Method vs Static Method**: Create a class `Student` with a class method `get_school_name()` and a static method `calculate_age()`. The class method should print the name of the school, and the static method should calculate age from birth year.
   
2. **Yield vs Return**: Write a generator function `count_up_to_n()` that yields numbers from 1 to `n`. 

3. **Partial Function**: Create a partial function that always adds 10 to a given number. Use `functools.partial` to define this function and call it with a number.

4. **Precision Handling**: Write a function that takes a float as input and returns the number rounded to two decimal places. 

---

### **Answer Key**

#### **1. Class Method vs Static Method**
```python
class Student:
    school_name = "ABC High School"

    @classmethod
    def get_school_name(cls):
        print(f"School: {cls.school_name}")

    @staticmethod
    def calculate_age(birth_year):
        return 2025 - birth_year

Student.get_school_name()  # Output: School: ABC High School
print(Student.calculate_age(2000))  # Output: 25
```

#### **2. Yield vs Return**
```python
def count_up_to_n(n):
    count = 1
    while count <= n:
        yield count
        count += 1

for number in count_up_to_n(3):
    print(number)
```

#### **3. Partial Function**
```python
from functools import partial

def add(x, y):
    return x + y

add_10 = partial(add, 10)
print(add_10(5))  # Output: 15
```

#### **4. Precision Handling**
```python
def round_number(value):
    return round(value, 2)

print(round_number(3.14159))  # Output: 3.14
```

---

### **Summary**
This lecture covered:
1. The basics of defining and using functions in Python.
2. Differences between class methods and static methods.
3. The `yield` keyword and how it works as a generator.
4. Returning multiple values from functions.
5. Using partial functions and first-class functions.
6. Handling precision in floating-point numbers.
7. Using `*args` and `**kwargs` for passing variable numbers of arguments.

This knowledge helps in creating efficient, flexible, and reusable code.
