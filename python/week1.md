# 🐍 Python Fundamentals: Week 1

This repository contains the core concepts and practice tasks for getting started with Python.

## 🧩 1. Variables and Types

### 💡 Concepts
- Dynamically typed: you don’t declare types explicitly.
- Everything is an object in Python.

### 📝 Examples
```python
x = 10          # int
y = 3.14        # float
name = "Mihir"  # str
active = True   # bool
```

#### Mental model: 
Think of variables as labels pointing to objects, not boxes holding values 

--- 

## 🔄 2. Expressions and Operators

In Python, expressions are combinations of values and operators that evaluate to a single value.

### 💡 Concepts
* **Arithmetic:** Used for mathematical calculations.
* **Comparison:** Used to compare two values (returns a boolean).
* **Logical:** Used to combine conditional statements.

### 🛠 Operator Reference
| Category | Operators | Description |
| :--- | :--- | :--- |
| **Arithmetic** | `+`, `-`, `*`, `/` | Basic Math |
| **Floor Division** | `//` | Division that rounds down to the nearest whole number |
| **Modulus** | `%` | Returns the remainder of a division |
| **Exponent** | `**` | Power (e.g., 2 to the power of 3) |
| **Comparison** | `==`, `!=`, `<`, `>`, `<=`, `>=` | Value comparisons |
| **Logical** | `and`, `or`, `not` | Logic gates |

### 📝 Examples
```python
# Floor division vs Normal division
print(5 / 2)    # 2.5
print(5 // 2)   # 2 (floor division)

# Power / Exponent
print(2 ** 3)   # 8

# Logical Operators
print(True and False)  # False
print(10 > 5 or 5 > 10) # True
```

#### Mental Model: 
Operators are actually methods under the hood. For example, writing ``a + b`` is the same as calling ```a.__add__(b)```.

---

## 📚 3. Collections
Choose your collection based on mutability and uniqueness needs.

### Lists: Ordered, mutable.

  Lists are Python's most versatile collection. They are used to store multiple items in a single variable.
  
  #### ⚙️ List Characteristics
  * **Ordered:** They maintain the order in which elements are inserted.
  * **Mutable:** You can change, add, and remove items after the list is created.
  * **Allows Duplicates:** Since lists are indexed, they can have items with the same value.
  * **Heterogeneous:** A single list can contain different data types (e.g., `[1, "Apple", True]`).
  
  #### 🛠 List Methods Reference
  
  | Method | Description | Example |
  | :--- | :--- | :--- |
  | `.append(x)` | Adds an item to the **end** of the list. | `fruits.append("orange")` |
  | `.extend(iterable)` | Adds all elements of a list (or any iterable) to the end. | `list1.extend(list2)` |
  | `.insert(i, x)` | Inserts an item at a **specific index** `i`. | `fruits.insert(1, "banana")` |
  | `.remove(x)` | Removes the **first occurrence** of value `x`. | `fruits.remove("apple")` |
  | `.pop([i])` | Removes and **returns** the item at index `i` (default is last). | `last_item = fruits.pop()` |
  | `.clear()` | Removes **all** items from the list. | `fruits.clear()` |
  | `.index(x)` | Returns the **index** of the first occurrence of `x`. | `pos = fruits.index("apple")` |
  | `.count(x)` | Returns the **number of times** `x` appears in the list. | `total = fruits.count("apple")` |
  | `.sort()` | Sorts the list in ascending order **in-place**. | `nums.sort()` |
  | `.reverse()` | Reverses the order of the list **in-place**. | `nums.reverse()` |
  | `.copy()` | Returns a **shallow copy** of the list. | `new_list = fruits.copy()` |
  
  #### ✂️ Advanced Feature: Slicing
  Slicing allows you to get a sub-section of a list using the syntax `list[start:stop:step]`.
  
  ```python
  nums = [0, 1, 2, 3, 4, 5]
  
  print(nums[1:4])    # [1, 2, 3] (Stop index is exclusive)
  print(nums[:3])     # [0, 1, 2] (From beginning)
  print(nums[::2])    # [0, 2, 4] (Every second element)
  print(nums[::-1])   # [5, 4, 3, 2, 1, 0] (Reverse shortcut)
  ```python
  nums = [1, 2, 3]
  nums.append(4)
  ```

### Tuples: ordered, immutable
```python
point = (10, 20)
```

### Sets: unique, unordered

```python
tags = {"python", "automation"}
```

### Dicts: Key-value pairs.
```python
user = {"name": "Mihir", "role": "QA Architect"}
```

#### Mental Model: 
Choose based on mutability and uniqueness needs.

--- 


