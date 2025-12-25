### Sets: unique, unordered

#### ⚙️ List Characteristics
  * **Unordered:** No guaranteed order of elements.
  * **Unique:** Automatically removes duplicates.
  * **Mutable:**  You can add or remove elements.
  * **Unindexed:**  You cannot access elements by index.

#### 📌 Creating Sets
```python
# Empty set (must use set(), not {})
s1 = set()

# Set with integers
s2 = {1, 2, 3}

# Set with mixed data types
s3 = {"apple", 42, 3.14}

# Duplicates are removed automatically
s4 = {1, 2, 2, 3, 3}
print(s4)  # {1, 2, 3}
```

#### 🎯 Basic Operations

```python

s = {1, 2, 3}

# Add element
s.add(4)

# Remove element
s.remove(2)   # ❌ error if not present
s.discard(5)  # ✅ safe, no error if not present

# Membership test
print(3 in s)  # True

```

#### 📜 Set Methods
Here’s the full list of commonly used methods:

 | Method | Description | Example |
  | :--- | :--- | :--- |
  | `.add(x)` | Add element. | `s.add(2)` |
  | `.remove(x)` | Returns `x`(error if not found). | `s.remove(1)` |
  | `.discard(x)` | Returns `x`(no error if not found). | `s.discard(1)` |
  | `.pop()` | Removes and returns a random element. | `s.pop()` |
  | `.clear(x)` | Removes all elements. | `s.clear(1)` |
  | `.copy()` | Returns a shallow copy. | `s.copy()` |
  | `.union(other)` | Returns union. | `s.unit({4,5})` |
  | `.intersection(other)` | Returns intersection. | `s.intersection({2,3})` |
  | `.difference(other)` | Returns difference. | `s.difference({2,3})` |  
  | `.symmetric_difference(other)` | Elements in either but not both. | `s.symmetric_difference({2,3})` |  
  | `.difference(other)` | Checks if set is subset. | `s.difference({2,3})` |  
  | `.issuperset(other)` | Checks if superset. | `s.issuperset({1,2})` |  
  | `.isdisjoint(other)` | True if no common elements. | `s.isdisjoint({10,11})` |  

#### ⚡ Advanced Features of Sets

##### 1. Set Operations (like Math)

```python
a = {1, 2, 3}
b = {3, 4, 5}

print(a | b)   # Union → {1,2,3,4,5}
print(a & b)   # Intersection → {3}
print(a - b)   # Difference → {1,2}
print(a ^ b)   # Symmetric difference → {1,2,4,5}
```

##### 2. Frozen Sets (Immutable Sets)

```python
fs = frozenset([1, 2, 3])
# fs.add(4) ❌ Error: frozenset is immutable

```

##### 3. Set Comprehension
```python
s = {x**2 for x in range(5)}
print(s)  # {0, 1, 4, 9, 16}
```

##### 4. Removing Duplicates from a List

```python
nums = [1, 2, 2, 3, 3, 4]
unique = set(nums)
print(unique)  # {1, 2, 3, 4}
```

### Dicts: Key-value pairs.
```python
user = {"name": "Mihir", "role": "QA Architect"}
```

#### Mental Model: 
Choose based on mutability and uniqueness needs.

--- 


