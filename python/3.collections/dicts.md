### 🧩 Dictionary: Ordered, mutable.

#### ⚙️ Characteristics
  * **Key–Value pairs:** Each item has a unique key and its associated value..
  * **Mutable:** You can add, update, or remove items.
  * **Keys must be immutable:** Keys must be immutable (e.g., strings, numbers, tuples).
  * **Values can be anything** (mutable or immutable).

#### 📌 Creating Dictionaries

```python
# Empty dictionary
d1 = {}

# With key-value pairs
d2 = {"name": "Mihir", "role": "Automation", "exp": 9}

# Using dict() constructor
d3 = dict(name="Alice", age=30)

# From list of tuples
d4 = dict([("x", 10), ("y", 20)])
```

#### 🎯 Accessing & Modifying

```python
person = {"name": "Mihir", "city": "Ahmedabad"}

print(person["name"])        # Mihir
print(person.get("age"))     # None (safe access)

# Add or update
person["age"] = 35

# Delete
del person["city"]

```

#### 📜 Methods

 | Method | Description | Example |
  | :--- | :--- | :--- |
  | `.get(key[,defalt])` | Safe access. | `d.get("x",0)` |
  | `.keys()` | Returns all keys. | `d.keys()` |
  | `.values()` | Returns all values. | `d.values()` |
  | `.items()` | Returns key-value pairs. | `d.items()` |
  | `.update(other)` | Merges another dict. | `d.update({"x":10})` |
  | `.pop(key[,default])` | Removes key and returns value. | `d.pop("x")` |
   | `.popitem()` | Removes last inserted pair. | `d.popitem()` |
   | `.clear()` | Removes all items. | `d.clear()` |
   | `.copy()` | Shallow copy. | `d.copy()` |
   | `.setdefault(key[,default])` | Returns value if key exists, else inserts default. | `d.setdefault("a",10)` |

#### ⚡Advanced Features of Dictionaries

##### 1. Dictionary Comprehension

```python 
squares = {x: x**2 for x in range(5)}
print(squares)  # {0:0, 1:1, 2:4, 3:9, 4:16}
```

##### 2. Nested Dictionaries

```python 
users = {
    "mihir": {"role": "Automation", "exp": 9},
    "alice": {"role": "DevOps", "exp": 5}
}
print(users["mihir"]["role"])  # Automation
```

##### 3. Using Tuples as Keys

```python 
coords = {}
coords[(10, 20)] = "Point A"
print(coords[(10, 20)])  # Point A
```


##### 4. Iterating

```python 
d = {"a": 1, "b": 2, "c": 3}

for key, value in d.items():
    print(key, value)
```

##### 5. Defaultdict (from `collections`)

```python 
from collections import defaultdict

dd = defaultdict(int)
dd["missing"] += 1
print(dd)  # {'missing': 1}
```

##### 6. OrderedDict (pre-3.7)
Before Python 3.7, dicts didn’t guarantee order. `OrderedDict` was used.
Now, normal dicts preserve insertion order.


##### 7. Counter (special dict)

```python
from collections import Counter

data = ["apple", "banana", "apple", "cherry"]
count = Counter(data)
print(count)  # {'apple': 2, 'banana': 1, 'cherry': 1}

```

