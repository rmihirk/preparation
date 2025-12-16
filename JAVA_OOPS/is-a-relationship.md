<em>

# Inheritance and the Object Class

If our class extends any other class, then our class is an indirect child class of Object. This structure forms multilevel inheritance.

**Example (Multilevel Inheritance):** Object → Class B → Class A (Valid)

If our class doesn't extend any other class, then our class is the direct child class of Object.

**Example (Direct Inheritance):** Class A → Object

## Multiple Inheritance in Classes

**Multiple Inheritance:** Having more than one parent class at the same level.

Parent 1 and Parent 2 → Child

In Java, any class can extend only one class at a time. Therefore, Java does not provide support for multiple inheritance between classes.

**Example (Invalid):**
```java
class C extends A, B {} // Invalid in Java
```

## The Ambiguity Problem

Java avoids multiple inheritance in classes because there is a chance of causing ambiguity problems (The Diamond Problem).

**Problem:** If Parent 1 and Parent 2 both contain a method with the same signature (`methodOne()`), the compiler cannot determine which inherited implementation should be used when `Child.methodOne()` is called.

## Interfaces and Ambiguity

### Why won't the ambiguity problem occur with multiple inheritance in Interfaces?

Interfaces contain method declarations (signatures) but historically no implementation (or only default/static implementations in modern Java). When a class implements multiple interfaces that define the same method, the implementing class is forced to provide a single, concrete implementation. Since no pre-existing code is inherited, there is no ambiguity.

**Example (Valid with Interfaces):**
```java
interface Inter1 { public void m1(); }
interface Inter2 { public void m1(); }
interface Inter3 extends Inter1, Inter2 {} // Valid: extends multiple interfaces

class Test implements Inter3 {
    public void m1() { 
        System.out.println("This is method m1"); 
    }
}
```

## Cyclic Inheritance

Cyclic inheritance is not allowed in Java.

**Example (Invalid):**
```java
class A extends B {}
class B extends A {} // Cyclic inheritance involving A and B
```

</em>
