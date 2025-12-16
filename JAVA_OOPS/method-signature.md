# Java OOP: Method Signatures, Polymorphism, and Overloading

## Method Signature

A method signature in Java consists of the method name followed by argument types.

**Example:**  `public void m1(int i, float f);`, the signature is `m1(int i, float f)`.

> **Note:** The return type is NOT part of the method signature. The compiler uses the method signature when resolving method calls.

### Method Signature Resolution Example

```java
class Test {
     public void m1(double d) {}
     public void m2(int i) {}

    public static void main(String args[]) {
        Test t = new Test();
        t.m1(10.5);     
        t.m2(10);    
        t.m3(10.5);  // C.E : Cannot find symbol m3(double)
    }
}
```

### Constraint

You cannot have two methods with the same signature in the same class.

```java
public void m1() {}
public int m1() {} // ❌ Compile-time error: Method m1() already defined
```

---


## Polymorphism

**Definition:** Same name with different forms.

### Types of Polymorphism

| Type | Category |
|------|----------|
| **Method Overloading** | Compile-time / Static / Early Binding |
| **Method Overriding** | Run-time / Dynamic / Late Binding |
| **Method Hiding** | Both |

### Parent Reference Example

```java
List l = new ArrayList();
List l = new LinkedList();
List l = new Vector();
List l = new Stack();
```
---


## Method Overloading

Two methods are overloaded if they have the **same name and different argument types**.

### Advantages

- Reduces programming complexity
- Improves code readability
- Unlike C, Java supports method overloading

### Method Overloading Example

```java
class Test {
    public static void main(String args[]) {
        Test t = new Test();
        t.m1();      // no-arg
        t.m1(10);    // int-arg
        t.m1(10.5);  // double-arg
    }
    
    public void m1() {
        System.out.println("no-arg");
    }
    
    public void m1(int i) {
        System.out.println("int-arg");
    }
    
    public void m1(double d) {
        System.out.println("double-arg");
    }
}
```
