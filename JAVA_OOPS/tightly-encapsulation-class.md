<em>

# Tightly Encapsulated Class

## Definition

A class is said to be tightly encapsulated if and only if every variable of that class declared as `private` whether the variable has getter and setter methods are not, and whether these methods declared as public or not, these checking are not required to perform.

## Tightly Encapsulated Check

### Example

```java
class A {
    private int x = 10;  // Valid - all variables are private
}

class B extends A {
    int y = 20;  // Invalid - y is not private
}

class C extends A {
    private int z = 30;  // Valid - all variables are private
}
```

## Important Note

If the parent class is not tightly encapsulated, no child class can be tightly encapsulated.


</em>
