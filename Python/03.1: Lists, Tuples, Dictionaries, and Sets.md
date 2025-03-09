
## **Lecture 4: Lists, Tuples, Dictionaries, and Sets**

### **1. Introduction to Data Structures**
Python provides built-in data structures to store collections of data. The most commonly used ones are:
- **Lists**
- **Tuples**
- **Dictionaries**
- **Sets**

---

### **2. Lists**

A **list** is a mutable, ordered collection of items.

#### **Creating Lists**
```python
my_list = [1, 2, 3, 4]
fruits = ['apple', 'banana', 'cherry']
```

#### **Accessing Elements**
```python
print(my_list[0])  # Output: 1
print(fruits[1])   # Output: banana
```

#### **List Operations**
- **Adding elements**: `.append()`, `.insert()`
```python
my_list.append(5)  # Adds 5 to the end
fruits.insert(1, 'orange')  # Adds 'orange' at index 1
```

- **Removing elements**: `.remove()`, `.pop()`
```python
my_list.remove(3)  # Removes 3
fruits.pop(1)      # Removes element at index 1 (orange)
```

- **List slicing**:
```python
sub_list = my_list[1:3]  # Slices from index 1 to 2
```

#### **Exercises on Lists:**
1. Create a list of your favorite movies and print the list.
2. Add a new movie to the list and remove an old movie.
3. Slice the list to show the first 3 movies.

---

### **3. Tuples**

A **tuple** is an immutable, ordered collection of items. Tuples cannot be changed once they are created.

#### **Creating Tuples**
```python
my_tuple = (1, 2, 3)
colors = ('red', 'green', 'blue')
```

#### **Accessing Elements**
```python
print(my_tuple[0])  # Output: 1
print(colors[2])    # Output: blue
```

#### **Tuple Operations**
Since tuples are immutable, you cannot modify them directly, but you can perform other operations like counting elements:
```python
print(colors.count('green'))  # Output: 1
```

#### **Exercises on Tuples:**
1. Create a tuple of 5 cities and print the tuple.
2. Access and print the second city from the tuple.
3. Count how many times a specific city appears in the tuple.

---

### **4. Dictionaries**

A **dictionary** is an unordered collection of key-value pairs. Keys must be unique, but values can be duplicated.

#### **Creating Dictionaries**
```python
my_dict = {'name': 'Alice', 'age': 25, 'city': 'New York'}
```

#### **Accessing Values**
```python
print(my_dict['name'])  # Output: Alice
print(my_dict.get('age'))  # Output: 25
```

#### **Adding/Modifying Items**
```python
my_dict['email'] = 'alice@example.com'  # Adding a new key-value pair
my_dict['age'] = 26  # Modifying the value for the key 'age'
```

#### **Removing Items**
```python
my_dict.pop('city')  # Removes the key 'city'
```

#### **Exercises on Dictionaries:**
1. Create a dictionary to store a student’s name, age, and grade. Print the dictionary.
2. Update the age of the student and add the address.
3. Remove the grade and print the dictionary.

---

### **5. Sets**

A **set** is an unordered collection of unique elements. It does not allow duplicates.

#### **Creating Sets**
```python
my_set = {1, 2, 3, 4}
fruits_set = {'apple', 'banana', 'cherry'}
```

#### **Adding and Removing Elements**
```python
my_set.add(5)  # Adds 5 to the set
fruits_set.remove('banana')  # Removes 'banana'
```

#### **Set Operations**
- **Union**: Combines two sets.
```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
print(set1 | set2)  # Output: {1, 2, 3, 4, 5}
```

- **Intersection**: Returns common elements between sets.
```python
print(set1 & set2)  # Output: {3}
```

- **Difference**: Returns elements in one set but not the other.
```python
print(set1 - set2)  # Output: {1, 2}
```

#### **Exercises on Sets:**
1. Create a set of your favorite fruits and add a new fruit to it.
2. Remove a fruit from the set.
3. Perform a union and intersection between two sets (one with fruits, the other with vegetables).

---

### **6. Comparing Data Structures**

- **Lists**: Ordered, mutable, allows duplicates.
- **Tuples**: Ordered, immutable, allows duplicates.
- **Dictionaries**: Unordered, mutable, stores key-value pairs.
- **Sets**: Unordered, mutable, no duplicates.

---

### **Practical Example:**

Let’s combine these data structures in a practical example. Imagine you are building a contact book.

```python
contact_book = {
    'John': {'phone': '1234567890', 'email': 'john@example.com'},
    'Alice': {'phone': '0987654321', 'email': 'alice@example.com'}
}

# Add a new contact
contact_book['Bob'] = {'phone': '5555555555', 'email': 'bob@example.com'}

# Update a contact's email
contact_book['John']['email'] = 'john_updated@example.com'

# Display all contacts
for name, details in contact_book.items():
    print(f"Name: {name}, Phone: {details['phone']}, Email: {details['email']}")
```

---

### **7. Additional Practice Problems:**

1. Write a Python program that counts the number of occurrences of each word in a given sentence using a dictionary.
2. Write a program to find the union and difference between two sets of numbers.
3. Create a list of numbers, then create a tuple with the same numbers and finally create a set from the list. Compare the three.

---

### **Summary:**

- **Lists** are ordered and mutable collections.
- **Tuples** are ordered but immutable.
- **Dictionaries** are unordered collections of key-value pairs.
- **Sets** are unordered collections with no duplicate elements.

---

