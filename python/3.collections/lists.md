### 🧩 Lists: Ordered, mutable.

  Lists are Python's most versatile collection. They are used to store multiple items in a single variable.
  
  #### ⚙️ Characteristics
  * **Ordered:** They maintain the order in which elements are inserted.
  * **Mutable:** You can change, add, and remove items after the list is created.
  * **Allows Duplicates:** Since lists are indexed, they can have items with the same value.
  * **Heterogeneous:** A single list can contain different data types (e.g., `[1, "Apple", True]`).

#### 📌 Creating List

```python
# Empty list
l1 = []

# List with integers
l2 = [1, 2, 3]

# Mixed data types
l3 = ["apple", 42, 3.14]

# Nested list
l4 = [1, [2, 3], [4, 5]]

```

#### 🎯 Accessing & Modifying

```python
fruits = ["apple", "banana", "cherry"]

print(fruits[0])    # apple
print(fruits[-1])   # cherry

# Modify
fruits[1] = "orange"
print(fruits)       # ['apple', 'orange', 'cherry']

```

  #### 📜 Methods
  
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
  
  #### ⚡ Advanced Feature: Slicing
  Slicing allows you to get a sub-section of a list using the syntax `list[start:stop:step]`.
  
  ```python
  nums = [0, 1, 2, 3, 4, 5]
  
  print(nums[1:4])    # [1, 2, 3] (Stop index is exclusive)
  print(nums[:3])     # [0, 1, 2] (From beginning)
  print(nums[::2])    # [0, 2, 4] (Every second element)
  print(nums[::-1])   # [5, 4, 3, 2, 1, 0] (Reverse shortcut)
  ```
