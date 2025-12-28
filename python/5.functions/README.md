<em>

### 🛠 Control Flow
Functions in Python are reusable blocks of code that perform a specific task. They help you organize, modularize, and avoid repetition in your programs.

- *Reusable*: Write once, use many times.
- *Organized*: Break large problems into smaller pieces.
- *Modular*: Makes code easier to maintain and test.
- *Encapsulated*: Logic is contained in one place.

#### 📌 Defining and Calling Functions
```python
# Defining a function
def greet(name):
    print(f"Hello, {name}!")

# Calling a function
greet("Mihir")   # Output: Hello, Mihir!
```
    - Use the def keyword to define.
    - Parameters allow input.
    - Functions can return values using return.

#### 🎯 Types of Functions
- Built-in functions: Already available (e.g., `len()`, `print()`, `sum()`).
- User-defined functions: Created with `def`.
- Lambda functions: Anonymous, single-line functions.

```python
square = lambda x: x**2
print(square(5))  # 25
```
- Recursive functions: Functions that call themselves.
```python
def factorial(n):
    return 1 if n == 0 else n * factorial(n-1)
```


#### 📜 Function Parameters
- Positional arguments: Matched by position.
- Keyword arguments: Matched by name.
- Default arguments: Provide fallback values.
- Variable-length arguments:
    - `*args` → tuple of extra arguments.
    - `**kwargs` → dict of extra keyword arguments.

```python
def demo(a, b=10, *args, **kwargs):
    print(a, b, args, kwargs)

demo(1, 2, 3, 4, x=5, y=6)
# Output: 1 2 (3,4) {'x':5,'y':6}

```

#### ⚡ Advanced Features

##### 1. Return Multiple Values

```python
def calc(x, y):
    return x+y, x*y

add, mul = calc(3, 4)
print(add, mul)  # 7 12
```

##### 2. Docstrings

```python
def greet(name):
    """This function greets the user by name."""
    print(f"Hello, {name}")
```

##### 3. Nested Functions

```python
def outer():
    print("Outer function")
    def inner():
        print("Inner function")
    inner()
outer()
```

##### 4. Closures

```python
def make_multiplier(n):
    def multiplier(x):
        return x * n
    return multiplier

double = make_multiplier(2)
print(double(5))  # 10
```

##### 5. Decorators
Functions that modify other functions:

```python
def decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper

@decorator
def say_hi():
    print("Hi")

say_hi()
```
<em>

