<em>

### 🧭 Control Flow
Control flow in Python determines how and when different parts of your code execute — using conditionals, loops, and exception handling. It lets you move beyond simple top-to-bottom execution and build logic that reacts to data, decisions, and errors

#### 🧩 Key Control Flow Structures

##### 1. Conditional Statements
- `if`: Executes a block if condition is true.
- `elif`: Adds more conditions.
- `else`: Executes if none of the above are true.

```python
x = 10
if x < 0:
    print("Negative")
elif x == 0:
    print("Zero")
else:
    print("Positive")
```

##### 2. Loops
- `for` loop: Iterates over sequences (lists, tuples, dicts, strings).
```python
for fruit in ["apple", "banana", "cherry"]:
    print(fruit)
```

- `while` loop: Repeats while condition is true.
```python
count = 0
while count < 3:
    print(count)
    count += 1
```
- Loop control keywords:
    - `break`: Exit loop early.
    - `continue`: Skip current iteration.

##### 3. Pattern Matching (match statement, Python 3.10+)

```python
status = 404
match status:
    case 200:
        print("OK")
    case 404:
        print("Not Found")
    case _:
        print("Unknown")
```

##### 4. Exception Handling
- `try … except`: Catch and handle errors.
- `finally`: Always runs (cleanup).

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
finally:
    print("Done")
```

##### 5. Other Control Flow Tools
- `return`: Exit a function and return a value.
- `yield`: Pause a generator function, resume later.
- `raise`: Trigger an exception.
- `with`: Context manager for safe resource handling.

</em>