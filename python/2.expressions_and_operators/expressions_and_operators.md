## 🔄 Expressions and Operators

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