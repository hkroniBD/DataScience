### **Lecture 5: Basic Operators in Python, Logical and Bitwise Operators, Ternary Operator, and OOP Concepts (Encapsulation, Inheritance, Polymorphism)**

---

### **1. Basic Operators in Python**
Operators in Python allow us to perform various operations on variables and values. Below are the commonly used operators:

#### **1.1 Arithmetic Operators**:
These operators are used to perform mathematical operations.
- **Addition (`+`)**: Adds two values.
  ```python
  x = 5 + 3  # Result: 8
  ```
- **Subtraction (`-`)**: Subtracts one value from another.
  ```python
  x = 5 - 3  # Result: 2
  ```
- **Multiplication (`*`)**: Multiplies two values.
  ```python
  x = 5 * 3  # Result: 15
  ```
- **Division (`/`)**: Divides one value by another, result is a float.
  ```python
  x = 5 / 2  # Result: 2.5
  ```
- **Floor Division (`//`)**: Divides and returns the quotient as an integer (rounded down).
  ```python
  x = 5 // 2  # Result: 2
  ```
- **Modulo (`%`)**: Returns the remainder after division.
  ```python
  x = 5 % 2  # Result: 1
  ```
- **Exponentiation (`**`)**: Raises one value to the power of another.
  ```python
  x = 5 ** 3  # Result: 125
  ```

#### **1.2 Comparison Operators**:
These operators compare two values and return a boolean result (`True` or `False`).
- **Equal to (`==`)**: Checks if two values are equal.
  ```python
  x = 5 == 5  # Result: True
  ```
- **Not equal to (`!=`)**: Checks if two values are not equal.
  ```python
  x = 5 != 3  # Result: True
  ```
- **Greater than (`>`)**: Checks if one value is greater than another.
  ```python
  x = 5 > 3  # Result: True
  ```
- **Less than (`<`)**: Checks if one value is less than another.
  ```python
  x = 5 < 10  # Result: True
  ```
- **Greater than or equal to (`>=`)**: Checks if one value is greater than or equal to another.
  ```python
  x = 5 >= 5  # Result: True
  ```
- **Less than or equal to (`<=`)**: Checks if one value is less than or equal to another.
  ```python
  x = 5 <= 7  # Result: True
  ```

#### **1.3 Logical Operators**:
Logical operators allow for combining multiple conditions.
- **And (`and`)**: Returns `True` if both conditions are `True`.
  ```python
  x = (5 > 3) and (3 < 10)  # Result: True
  ```
- **Or (`or`)**: Returns `True` if at least one condition is `True`.
  ```python
  x = (5 > 10) or (3 < 10)  # Result: True
  ```
- **Not (`not`)**: Reverses the boolean value.
  ```python
  x = not(5 > 10)  # Result: True
  ```

---

### **2. Bitwise Operators**
Bitwise operators perform operations on the binary representation of numbers.

- **AND (`&`)**: Performs bitwise AND.
  ```python
  x = 5 & 3   # Binary: 0101 & 0011 = 0001; Result: 1
  ```
- **OR (`|`)**: Performs bitwise OR.
  ```python
  x = 5 | 3   # Binary: 0101 | 0011 = 0111; Result: 7
  ```
- **XOR (`^`)**: Performs bitwise XOR (exclusive OR).
  ```python
  x = 5 ^ 3   # Binary: 0101 ^ 0011 = 0110; Result: 6
  ```
- **NOT (`~`)**: Performs bitwise NOT (inverts the bits).
  ```python
  x = ~5      # Binary: ~0101 = 1010; Result: -6
  ```
- **Left Shift (`<<`)**: Shifts the bits to the left by the specified number of positions.
  ```python
  x = 5 << 2  # Binary: 0101 << 2 = 010100; Result: 20
  ```
- **Right Shift (`>>`)**: Shifts the bits to the right by the specified number of positions.
  ```python
  x = 5 >> 2  # Binary: 0101 >> 2 = 0001; Result: 1
  ```

---

### **3. Ternary Operator**
Python supports a shorthand way of writing conditional expressions, known as the **ternary operator** or **conditional expression**.

Syntax:
```python
value_if_true if condition else value_if_false
```

- **Example**:
  ```python
  x = 10
  result = "Even" if x % 2 == 0 else "Odd"
  print(result)  # Output: Even
  ```

---

### **4. Object-Oriented Programming (OOP) in Python**
OOP is a programming paradigm based on the concept of objects, which contain both data and functions.

#### **4.1 Encapsulation**
Encapsulation is the bundling of data and the methods that operate on that data into a single unit (class), and restricting access to some of the object's components.

- **Private Variables**: Variables that are intended to be accessed only within the class.
  - To indicate private variables, we use a double underscore (`__`) before the variable name.
  ```python
  class Car:
      def __init__(self, model, year):
          self.__model = model   # Private variable
          self.__year = year     # Private variable

      def get_model(self):
          return self.__model

  car = Car("Tesla", 2020)
  print(car.get_model())  # Output: Tesla
  ```

#### **4.2 Inheritance**
Inheritance allows a class (child class) to inherit attributes and methods from another class (parent class).

- **Example**:
  ```python
  class Animal:
      def speak(self):
          print("Animal speaks")

  class Dog(Animal):
      def bark(self):
          print("Woof!")

  dog = Dog()
  dog.speak()  # Inherited from Animal class
  dog.bark()   # Defined in Dog class
  ```

#### **4.3 Polymorphism**
Polymorphism allows different classes to define methods that are called the same, but may behave differently.

- **Example**:
  ```python
  class Dog:
      def sound(self):
          print("Bark")
          
  class Cat:
      def sound(self):
          print("Meow")
  
  animals = [Dog(), Cat()]
  for animal in animals:
      animal.sound()  # Output: Bark, Meow (polymorphism in action)
  ```

---

### **5. Operator Overloading in Python**
Operator overloading allows you to define or alter the behavior of operators (`+`, `-`, `*`, etc.) for objects of a class.

- **Example** (Overloading `+` operator):
  ```python
  class Point:
      def __init__(self, x, y):
          self.x = x
          self.y = y

      def __add__(self, other):
          return Point(self.x + other.x, self.y + other.y)

      def __repr__(self):
          return f"Point({self.x}, {self.y})"

  point1 = Point(1, 2)
  point2 = Point(3, 4)
  result = point1 + point2  # Calls __add__ method
  print(result)  # Output: Point(4, 6)
  ```

---

### **6. `any()` and `all()` in Python**
- **`any()`**: Returns `True` if at least one element in an iterable is `True`.
  ```python
  x = [False, True, False]
  print(any(x))  # Output: True
  ```

- **`all()`**: Returns `True` if all elements in an iterable are `True`.
  ```python
  x = [True, True, False]
  print(all(x))  # Output: False
  ```

---

### **Assignments:**
1. **Ternary Operator Exercise**: Write a program to check whether a number is positive or negative using the ternary operator.
2. **Inheritance and Polymorphism Exercise**: Implement a parent class `Shape` with methods to calculate the area. Create subclasses `Circle` and `Rectangle` that inherit from `Shape` and implement the `area` method.
3. **Operator Overloading Exercise**: Overload the `-` operator for a class `Vector` that allows subtraction of two vector objects.

---

This lecture covers key concepts of Python operators, logical and bitwise operations, the ternary operator, and core object-oriented principles including encapsulation, inheritance, and polymorphism. It also introduces operator overloading and the built-in functions `any()` and `all()`.
