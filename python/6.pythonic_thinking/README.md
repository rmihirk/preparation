<em>

### 🛠 Pythonic Thinking
Pythonic thinking means writing code that embraces Python’s philosophy: clean, simple, readable, and leveraging the language’s strengths instead of forcing other paradigms. It’s not just about syntax — it’s about how you think and solve problems in Python.

- *Readability counts*: Code should be easy to read and understand.
- *Simplicity over complexity*: Prefer straightforward solutions.
- *Explicit is better than implicit*: Make behavior clear.
- *Use built-ins and idioms*: Don’t reinvent the wheel.
- *Leverage Python’s dynamic features*: Comprehensions, unpacking, context managers.

#### 📌 Examples of Pythonic vs Non-Pythonic Code

| Task | Non-Pythonic | Pythonic|
| :--- | :--- | :--- |
| Looping through list |<pre>for i in range(len(items)):<br> print(items[i])</pre>|<pre>for item in items:<br> print(item)</pre>|
| Swapping values |<pre>temp = a:<br>a = b<br>b = temp</pre>|<pre>a, b = b, a</pre>|
| Building a list |<pre>squares = []<br>for x in range(5):<br>squares.append(x**2)</pre>|<pre> squares = [x**2 for x in range(5)]</pre> |
| File handling |<pre>f = open("data.txt");<br>data = f.read();<br>f.close()></pre>|<pre>with open("data.txt") as f:<br>data = f.read()</pre>|

#### 🎯Key Pythonic Features

##### 1. Comprehensions
- List, set, and dict comprehensions for concise transformations.

```python
squares = {x: x**2 for x in range(5)}
```

##### 2. Unpacking

```python
a, b, c = (1, 2, 3)
```

Extended unpacking:

```python
first, *middle, last = [1,2,3,4,5]
```

##### 3. EAFP (Easier to Ask Forgiveness than Permission)
- Instead of checking everything upfront, just try and handle exceptions:

```python
try:
    value = my_dict["key"]
except KeyError:
    value = None
```

##### 4. Duck Typing

```python
def process(x):
    x.append(10)   # Works if x behaves like a list
```

##### 5. Use of Built-ins

Prefer `sum()`, `any()`, `all()`, `enumerate()`, `zip()` over manual loops.

#### ⚡ Advanced Pythonic Practices

- **Decorators**: Add functionality without modifying code.
- **Context Managers (with)**: Handle resources safely.
- **Generators (yield)**: Efficient iteration.
- **Itertools & functools**: Functional-style utilities.
- **Readable naming & docstrings**: Self-documenting code.

##### 1. Comprehensions Everywhere
- List, Set, Dict comprehensions replace verbose loops.

```python
# List comprehension
squares = [x**2 for x in range(10)]

# Dict comprehension
mapping = {x: x**2 for x in range(5)}

# Set comprehension
unique = {char for char in "automation"}
```
👉 Cleaner, faster, and more expressive than manual loops.

##### 2. Enumerate and Zip

- Use `enumerate()` instead of manual counters.

```python
for i, val in enumerate(["a", "b", "c"]):
    print(i, val)
```

- Use `zip()` to iterate multiple sequences together.

```python
names = ["Mihir", "Alice"]
roles = ["Automation", "DevOps"]
for n, r in zip(names, roles):
    print(f"{n} → {r}")
```

##### 3. EAFP (Easier to Ask Forgiveness than Permission)
- Pythonic style prefers try/except over pre-checks.

```python
try:
    value = my_dict["key"]
except KeyError:
    value = None
```

##### 4. Context Managers (with)

- Handle resources safely without manual cleanup.
```python
with open("data.txt") as f:
    data = f.read()
```
👉 Ensures file closes automatically, even on errors.

##### 5. Generators and Iterators
- Use `yield` for memory-efficient iteration.

```python
def generate_numbers(n):
    for i in range(n):
        yield i
```

👉 Useful for large datasets or streaming automation logs.

##### 6. Decorators
- Functions that wrap other functions to add behavior.

```python
def logger(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@logger
def greet(name):
    print(f"Hello {name}")
```

👉 Perfect for logging, retries, or timing in automation frameworks.

##### 7. Functional Tools
- Built-ins like map(), filter(), reduce() (from functools).

```python 
from functools import reduce
nums = [1,2,3,4]
product = reduce(lambda x,y: x*y, nums)
```

👉 Concise functional-style programming.

##### 8. Advanced Data Structures
- collections module: defaultdict, Counter, OrderedDict, namedtuple.
- dataclasses (Python 3.7+) for lightweight classes.

```python 
from dataclasses import dataclass

@dataclass
class TestConfig:
    browser: str
    version: str
```