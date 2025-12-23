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
Operators are actually methods under the hood. For example, writing `a + b` is the same as calling `a.__add__(b)`.

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
  ```

### Tuples: ordered, immutable

 #### ⚙️ List Characteristics
  * **Ordered:** Elements have a fixed position.
  * **Immutable:** Once created, you cannot change, add, or remove elements.
  * **Indexed:** Access elements by index (starting at 0).
  * **Heterogeneous:** Can store different data types (int, str, float, etc.).
    
 #### 🛠 List Methods Reference
Tuples are deliberately minimal because they’re immutable. They only have two built-in methods:

 | Method | Description | Example |
  | :--- | :--- | :--- |
  | `.count(x)` | Returns the **number of times** `x` appears in the tuple. | `(1,2,3,4,1).count(1)` |
  | `.tuple.index(x, start, end)` | Returns a **index** of the x. | `(1,2,3,4,1).index(2,0,4)` |

- That’s it — unlike lists, tuples don’t have .append(), .remove(), etc., because they cannot be modified

 #### ✂️ Advanced Feature of Tuples

 ##### 1. Tuple Packing & Unpacking
```python
 # Packing
t = 1, "apple", 3.14

# Unpacking
a, b, c = t
print(a, b, c)  # 1 apple 3.14
```

Supports extended unpacking:
```python
t = (1, 2, 3, 4, 5)
a, *b, c = t
print(a)  # 1
print(b)  # [2, 3, 4]
print(c)  # 5
```
**Note** : Multiple * not allowed 

##### 2. Tuples as Dictionary Keys
Because tuples are immutable and hashable:
```python
coords = {}
coords[(10, 20)] = "Point A"
print(coords[(10, 20)])  # Point A
```

##### 3. Tuples as Dictionary Keys
Tuples can contain other tuples:
```python
nested = ((1, 2), (3, 4), (5, 6))
print(nested[1][0])  # 3
```

##### 4.  Tuple with `*args` in Functions
Tuples naturally appear when using variable-length arguments:

```python
def demo(*args):
    print(args)  # args is a tuple

demo(1, "apple", True)  # (1, 'apple', True)
```

##### 5.  Memory Efficienc
Tuples are more memory-efficient than lists:
```python
import sys
print(sys.getsizeof([1,2,3]))  # larger
print(sys.getsizeof((1,2,3)))  # smaller

```

##### 6.  Named Tuples (from `collections`)
Adds readability by giving names to tuple elements

```python
from collections import namedtuple

Point = namedtuple("Point", ["x", "y"])
p = Point(10, 20)
print(p.x, p.y)  # 10 20
```

##### 7. Tuple Comprehension Trick
Tuples don’t support comprehension directly, but you can wrap a generator in `tuple()`.

```python
t = tuple(x**2 for x in range(5))
print(t)  # (0, 1, 4, 9, 16)
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


