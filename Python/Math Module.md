The `math` module in Python provides mathematical functions such as logarithms, trigonometry, factorials, and other advanced math operations.

## **1. Importing the Math Module**
```python
import math
```

---

## **2. Commonly Used Functions**

### **A. Basic Mathematical Functions**
| Function | Description | Example |
|----------|------------|---------|
| `math.sqrt(x)` | Returns the square root of `x` | `math.sqrt(16) → 4.0` |
| `math.pow(x, y)` | Returns `x` raised to the power `y` | `math.pow(2, 3) → 8.0` |
| `math.exp(x)` | Returns `e^x` (exponential) | `math.exp(2) → 7.389` |
| `math.log(x)` | Returns natural logarithm (base `e`) | `math.log(10)` |
| `math.log10(x)` | Returns logarithm base 10 | `math.log10(100) → 2.0` |
| `math.log2(x)` | Returns logarithm base 2 | `math.log2(8) → 3.0` |
| `math.factorial(x)` | Returns factorial of `x` | `math.factorial(5) → 120` |

---

### **B. Trigonometric Functions (Radians)**
| Function | Description | Example |
|----------|------------|---------|
| `math.sin(x)` | Returns sine of `x` (radians) | `math.sin(math.pi/2) → 1.0` |
| `math.cos(x)` | Returns cosine of `x` (radians) | `math.cos(0) → 1.0` |
| `math.tan(x)` | Returns tangent of `x` (radians) | `math.tan(math.pi/4) → 1.0` |
| `math.asin(x)` | Returns arcsin of `x` | `math.asin(1) → π/2` |
| `math.acos(x)` | Returns arccos of `x` | `math.acos(1) → 0.0` |
| `math.atan(x)` | Returns arctan of `x` | `math.atan(1) → π/4` |

**Convert Degrees to Radians and Vice Versa**
```python
math.radians(180)  # 3.14159 (π)
math.degrees(math.pi)  # 180.0
```

---

### **C. Rounding and Absolute Functions**
| Function | Description | Example |
|----------|------------|---------|
| `math.ceil(x)` | Rounds `x` up to nearest integer | `math.ceil(4.3) → 5` |
| `math.floor(x)` | Rounds `x` down to nearest integer | `math.floor(4.9) → 4` |
| `math.trunc(x)` | Truncates the decimal part | `math.trunc(4.7) → 4` |
| `math.fabs(x)` | Returns absolute value | `math.fabs(-7.5) → 7.5` |

---

### **D. Constants in `math` Module**
| Constant | Description | Value |
|----------|------------|-------|
| `math.pi` | The mathematical constant π | `3.141592653589793` |
| `math.e` | Euler’s number `e` | `2.718281828459045` |
| `math.tau` | `τ = 2π` | `6.283185307179586` |
| `math.inf` | Represents infinity | `math.inf` |
| `math.nan` | Not a Number | `math.nan` |

---

## **3. Example Usage**
```python
import math

# Using sqrt() and factorial()
print(math.sqrt(25))        # 5.0
print(math.factorial(5))    # 120

# Using trigonometric functions
print(math.sin(math.radians(30)))  # 0.5

# Using constants
print(math.pi)  # 3.141592653589793
```

Would you like a detailed explanation of any specific function? 🚀
