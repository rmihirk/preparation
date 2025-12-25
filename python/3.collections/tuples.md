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
