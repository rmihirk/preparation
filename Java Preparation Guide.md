# Java Preparation Guide

## Q.1 Difference between final, finally, finalize?

**Final:**
- Modifier applicable to classes, methods, and variables
- Final class: Cannot be extended (no subclass creation)
- Final method: Cannot be overridden in child classes
- Final variable: Becomes a constant; no reassignment allowed

**Finally:**
- Block associated with try-catch for cleanup code
- Always executes whether exception occurs or not
```java
try {
    // risky code
} catch (Exception e) {
    // handling code
} finally {
    // cleanup code (always executes)
} 
```

**Finalize():**
- Method invoked by garbage collector before object destruction
- Used for cleanup activities related to object resources
- Note: Finally is for try-block cleanup; finalize() is for object cleanup

---

## Q.2 Difference between String Literal and new String Object?

Both create String objects with key differences:

| Aspect | String Literal | new String() |
|--------|---|---|
| Memory Location | String Pool (Heap) | Heap Memory |
| Reuse | May return existing object | Always creates new object |
| Performance | Better (reuses objects) | Slower (always creates new) |

```java
String strObject = new String("Java");    // Heap Memory
String strLiteral = "Java";               // String Pool (Heap)
```

**PermGen Space (Java 7 and earlier):**
- PermGen = Permanent Generation
- Separate from main heap; stores class metadata, static content, bytecode
- String Pool was in PermGen before Java 8 (now in regular heap)

---

## Q.3 Difference Between String vs StringBuffer

| Property | String | StringBuffer |
|----------|--------|--------------|
| Mutability | Immutable | Mutable |
| Modification Behavior | Creates new object on change | Modifies existing object |
| Performance | Slower (new objects created) | Faster (in-place modification) |
| Thread-Safe | Yes (immutable) | Yes (synchronized methods) |

```java
String s = new String("Mihir");
s.concat("Rathod");
System.out.println(s); // Mihir (unchanged)

StringBuffer sb = new StringBuffer("Mihir");
sb.append("Rathod");
System.out.println(sb); // MihirRathod (changed)
```

---

## Q.4 Difference between '==' and 'equals()' Method

| Operator/Method | Purpose | Use Case |
|---|---|---|
| == | Reference comparison | Compare object references |
| equals() | Content comparison (when overridden) | Compare object values |

```java
String s1 = new String("Mihir");
String s2 = new String("Mihir");

System.out.println(s1 == s2);           // false (different references)
System.out.println(s1.equals(s2));      // true (same content)
```

**Note:** The equals() method in String, wrapper classes, and collection classes is overridden for content comparison.

---

## Q.5 Difference between StringBuffer (1.0v) and StringBuilder (1.5v)

| Feature | StringBuffer | StringBuilder |
|---------|--------------|---------------|
| Synchronization | All methods synchronized | No synchronization |
| Thread-Safety | Thread-safe | Not thread-safe |
| Performance | Lower (thread overhead) | Higher (no synchronization) |
| Use Case | Multi-threaded environments | Single-threaded environments |
| Introduced | Java 1.0 | Java 1.5 |

**When to use:**
- **String:** Fixed content that won't change
- **StringBuffer:** Mutable content + thread safety required
- **StringBuilder:** Mutable content + thread safety NOT required

---

## Q.6 Interface vs Abstract Class vs Concrete Class

| Type | Abstraction Level | Implementation | Use Case |
|------|-------------------|---|---|
| Interface | 100% | None (before Java 8) | Pure contract/specification |
| Abstract Class | Partial | Partial | Partial implementation with common code |
| Concrete Class | 0% | Complete | Ready-to-use implementation |

---

## Q.7 Access Specifiers & Access Modifiers

In Java, there is no distinction between "specifiers" and "modifiers"—all are considered modifiers:
- `public`, `private`, `protected`, `default`
- `static`, `final`, `abstract`, `synchronized`, etc.

Example of invalid syntax:
```java
private class Test { }  // Compile Error: Modifier private not allowed here
```

---

## Q.8 Difference between Interface and Abstract Class

| Aspect | Interface | Abstract Class |
|--------|-----------|---|
| Abstraction | 100% pure abstract | Partial implementation |
| Method Visibility | Always public and abstract | Can be any access level |
| Method Modifiers Restrictions | Cannot use: private, protected, final, static, synchronized, native, strictfp | No restrictions |
| Variables | Always public, static, final | No restrictions |
| Variable Initialization | Compulsory at declaration | Not required |
| Blocks | Cannot declare instance/static blocks | Can declare blocks |
| Constructors | Cannot declare | Can declare |

---

## Q.9 Interface Enhancements (Java 8+)

### Default Methods
- Help extend interfaces without breaking implementation classes
- Bridge differences between interfaces and abstract classes
- Enable lambda expression support in Collections API

```java
public interface MyInterface {
    default void defaultMethod() {
        // default implementation
    }
}
```

### Static Methods (Java 8+)
```java
public interface MyInterface {
    static void staticMethod() {
        // static implementation
    }
}
```

**Benefits:**
- Avoid utility classes
- Provide default implementations
- Implementation classes choose what to override
- Also called "Defender Methods" or "Virtual Extension Methods"

---

## Q.10 Explain System.out.println()

```java
class System {
    static PrintStream out;
}

System.out.println("Hello");
```

- **System:** Class in java.lang package
- **out:** Static variable of type PrintStream
- **println():** Method in PrintStream class

---

## Q.11 Difference between Overloading and Overriding

### Overloading (Compile-time Polymorphism)

| Property | Requirement |
|----------|---|
| Method Names | Must be same |
| Arguments | Must be different (type, number, or order) |
| Return Type | No restriction |
| Applicable to | All methods (including private, static, final) |

```java
class Test {
    public void m1(int i) { }
    public void m1(long l) { }
}
```

### Overriding (Runtime Polymorphism)

| Property | Requirement |
|----------|---|
| Method Names | Must be same |
| Arguments | Must be same (type, number, and order) |
| Return Type | Must be same (covariant types allowed since Java 1.5) |
| Access Modifier | Can be increased, not decreased |
| Exception Throw | No new checked exceptions; unchecked exceptions allowed |
| Applicable to | Non-static, non-final, non-private methods |

```java
class Parent {
    public void marry() {
        System.out.println("Subba Laxmi");  // overridden method
    }
}

class Child extends Parent {
    public void marry() {
        System.out.println("Trisha Laxmi");  // overriding method
    }
}
```

**Method Resolution:**
- Overloading: Compiler (based on reference type)
- Overriding: JVM (based on runtime object)

---

## Q.12 Difference: Parent p=new Child() vs Child c=new Child()

| Scenario | Child c = new Child() | Parent p = new Child() |
|----------|---|---|
| Use Case | Know exact runtime type | Don't know exact runtime type (Polymorphism) |
| Method Access | Parent + Child methods | Only Parent class methods |
| Reference Flexibility | Only for that specific child class | Can hold any child class object |
| Best Practice | Less common | Recommended (Polymorphic approach) |

---

## Q.13 Try-Catch-Finally Rules

1. `try` requires `catch` or `finally` (or both)
2. `catch` requires `try` (cannot stand alone)
3. `finally` requires `try`
4. Order matters: try → catch → finally
5. Multiple catch blocks allowed (must be child-to-parent order)
6. Nesting of try-catch-finally is valid
7. Curly braces are mandatory

---

## Q.14 Exception vs Error

### Exception
- **Cause:** Usually caused by program logic
- **Recovery:** Recoverable
- **Example:** FileNotFoundException, NullPointerException

### Error
- **Cause:** System resource shortage
- **Recovery:** Non-recoverable
- **Example:** OutOfMemoryError, StackOverflowError

---

## Q.15 Checked vs Unchecked Exceptions

### Checked Exception
- Checked by compiler at compile-time
- Must be handled or declared
- Examples: IOException, SQLException, FileNotFoundException

### Unchecked Exception
- Not checked by compiler
- No requirement to handle
- Extends RuntimeException
- Examples: ArithmeticException, NullPointerException, ArrayIndexOutOfBoundsException

**Note:** All exceptions occur at runtime; none at compile-time.

---

## Q.16 Fully Checked vs Partially Checked Exceptions

- **Fully Checked:** All child classes are also checked (e.g., IOException)
- **Partially Checked:** Some child classes are unchecked (e.g., Exception, Throwable)

---

## Q.17 Control Flow in Try-Catch-Finally

```java
try {
    Statement 1;
    Statement 2;
    Statement 3;
} catch (X e) {
    Statement 4;
} finally {
    Statement 5;
}
Statement 6;
```

| Case | Scenario | Execution |
|------|----------|---|
| 1 | No exception | 1→2→3→5→6 (Normal) |
| 2 | Exception at 2, matched | 1→4→5→6 (Normal) |
| 3 | Exception at 2, not matched | 1→5→... (Abnormal) |
| 4 | Exception in catch block | Abnormal (finally still executes) |

**Key Points:**
- Finally always executes (even if exception in catch)
- Keep try blocks minimal (only risky code)
- If exception outside try block → always abnormal termination

---

## Q.18 Marker Interfaces

Empty interfaces with no methods or fields. Used to mark classes with special behavior.

### Serializable Interface
- Package: java.io
- Purpose: Makes object serializable (convertible to byte stream)
- Serialization: Object → Byte Stream (to file/database)
- Deserialization: Byte Stream → Object (from file/database)

### Cloneable Interface
- Package: java.lang
- Purpose: Creates replica of object with different name
- Requirement: Must override clone() method as public
- Exception: Throws CloneNotSupportedException if not implemented

### Remote Interface
- Package: java.rmi
- Purpose: Marks object as remote (accessible from another machine)
- Implementation: Extend UnicastRemoteObject or use exportObject()

---

## Q.19 APIs (Application Programming Interface)

Set of functions enabling interaction between software applications; supports data exchange.

### Types:
1. **SOAP** (Simple Object Access Protocol)
   - Uses HTTP + XML
   - More verbose, complex

2. **REST** (Representational State Transfer)
   - Uses HTTP + JSON/XML
   - Simpler, lightweight
   - Methods: GET, PUT, POST, DELETE

### API Testing Tools:
- Postman, SoapUI, Rest Template, Jersey, JMeter, Rest Assured

### Rest Assured (Java Framework)
- Framework for testing REST APIs
- Works with Maven/Gradle, JUnit/TestNG
- Java-specific REST API testing

---

## Q.20 Throw vs Throws

### Throw
- **Purpose:** Explicitly throw exception in code
- **Exception Type:** Only unchecked exceptions
- **Count:** Single exception at a time
- **Location:** Inside method body

```java
throw new ArithmeticException("Unable to proceed");
```

### Throws
- **Purpose:** Declare exceptions in method signature
- **Exception Type:** Both checked and unchecked
- **Count:** Multiple exceptions
- **Location:** Method signature

```java
public static int method() throws ArithmeticException, IOException { }
```

---

## Q.21 Maven Build Lifecycle

1. **Validate:** Verify project correctness and necessary information
2. **Compile:** Compile source code
3. **Test:** Run unit tests
4. **Package:** Package compiled code (JAR, WAR, etc.)
5. **Verify:** Verify integration tests and quality criteria
6. **Install:** Install package to local repository
7. **Deploy:** Deploy to remote repository for sharing

---

## Q.22 Decorator Pattern

Structural pattern allowing dynamic behavior addition to objects without affecting others.

### Key Principles:
- Wraps objects for functionality extension
- Follows Open/Closed Principle
- Supports multiple decorator combination

### Components:
1. **Component Interface:** Base interface for decorated objects
2. **Concrete Component:** Original object
3. **Decorator Class:** Implements component, holds reference, adds behavior
4. **Concrete Decorators:** Specific implementations

### Example: Coffee Shop
```java
interface Coffee {
    String getDescription();
    double cost();
}

class SimpleCoffee implements Coffee {
    public String getDescription() { return "Simple Coffee"; }
    public double cost() { return 5.00; }
}

abstract class CoffeeDecorator implements Coffee {
    protected Coffee decoratedCoffee;
    
    public CoffeeDecorator(Coffee coffee) {
        this.decoratedCoffee = coffee;
    }
    
    public String getDescription() {
        return decoratedCoffee.getDescription();
    }
    
    public double cost() {
        return decoratedCoffee.cost();
    }
}

class MilkDecorator extends CoffeeDecorator {
    public MilkDecorator(Coffee coffee) { super(coffee); }
    
    public String getDescription() {
        return decoratedCoffee.getDescription() + ", Milk";
    }
    
    public double cost() {
        return decoratedCoffee.cost() + 1.50;
    }
}
```

### Usage:
```java
Coffee coffee = new SimpleCoffee();
coffee = new MilkDecorator(coffee);
coffee = new SugarDecorator(coffee);
System.out.println(coffee.getDescription() + " $" + coffee.cost());
```

**Benefits:**
- Flexible alternative to subclassing
- Single Responsibility Principle
- Composition over inheritance
- Dynamic behavior combination

---

## Q.23 OOP Concepts in Java

### Four Main Principles:

1. **Encapsulation**
   - Bundle data (variables) and methods into single class
   - Restrict direct access via access modifiers
   - Example: Private variables with public getters/setters

2. **Inheritance**
   - New class inherits properties from existing class
   - Promotes code reuse
   - Example: `class Child extends Parent`

3. **Polymorphism**
   - Present same interface for different data types
   - **Compile-time:** Method overloading
   - **Runtime:** Method overriding

4. **Abstraction**
   - Hide complex implementation details
   - Show only essential features
   - Achieved via interfaces and abstract classes

---

## Q.24 Java Collections Framework

### Overview:
Framework providing classes and interfaces for storing and manipulating object groups.

### Main Collection Types:

**List** (Ordered, allows duplicates)
- ArrayList, LinkedList, Vector
- Access: by index

**Set** (Unordered, no duplicates)
- HashSet, TreeSet, LinkedHashSet
- Unique elements only

**Map** (Key-value pairs)
- HashMap, TreeMap, LinkedHashMap
- Each key maps to one value

---

## Q.25 Exception Handling & Custom Exceptions

### Exception Hierarchy:
```
Throwable
├── Exception (Checked/Unchecked)
└── Error (Unchecked)
```

### Custom Exception:
```java
public class CustomException extends Exception {
    public CustomException(String message) {
        super(message);
    }
}

// Usage
throw new CustomException("Custom error message");
```

---

## Q.26 Java Streams API (Java 8+)

### Overview:
Functional and declarative approach to process collections in parallel or sequentially.

### Key Concepts:

1. **Source:** Collection (List, Set, Array)
2. **Intermediate Operations:** Filter, map, sorted (lazy - don't execute until terminal op)
3. **Terminal Operations:** forEach, collect, reduce (eager - trigger processing)

### Common Operations:
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

names.stream()
    .filter(n -> n.length() > 3)          // filter
    .map(String::toUpperCase)              // map
    .sorted()                              // sorted
    .forEach(System.out::println);         // forEach (terminal)
```

### Collect Example:
```java
List<String> upperNames = names.stream()
    .map(String::toUpperCase)
    .collect(Collectors.toList());
```

### Benefits:
- Concise, readable code
- Lazy evaluation improves performance
- Parallel processing: `.parallelStream()`
- Functional programming style

---

## Q.27 Lambda Expressions (Java 8+)

### Purpose:
Express single-method interfaces compactly without verbose anonymous classes.

### Syntax:
```
(parameters) -> { body }
```

### Examples:
```java
// No parameters
Runnable r = () -> System.out.println("Hello");

// Single parameter
Function<Integer, Integer> square = x -> x * x;

// Multiple parameters
Comparator<Integer> comp = (a, b) -> a - b;

// With body
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
numbers.forEach(n -> {
    if (n % 2 == 0) {
        System.out.println(n);
    }
});
```

### With Streams:
```java
numbers.stream()
    .filter(n -> n % 2 == 0)
    .map(n -> n * n)
    .forEach(n -> System.out.println(n));
```

### Functional Interfaces:
- Comparator, Runnable, Callable, Consumer, Supplier, Function, Predicate
- Custom: `@FunctionalInterface` annotation

---

## Q.28 Comparable vs Comparator

### Comparable Interface

- **Package:** java.lang
- **Method:** `compareTo(Object o)`
- **Purpose:** Define natural ordering within class
- **Implementation:** Class implements Comparable

```java
class Student implements Comparable<Student> {
    int rollNumber;
    String name;
    
    public int compareTo(Student other) {
        return this.rollNumber - other.rollNumber;  // ascending order
    }
}

Collections.sort(students);  // Uses Comparable
```

### Comparator Interface

- **Package:** java.util
- **Method:** `compare(Object o1, Object o2)`
- **Purpose:** Define custom sorting order (multiple criteria)
- **Implementation:** Separate class or lambda

```java
List<Student> students = Arrays.asList(...);

// Using lambda
students.sort((s1, s2) -> s1.rollNumber - s2.rollNumber);

// Using Comparator class
Collections.sort(students, new Comparator<Student>() {
    public int compare(Student s1, Student s2) {
        return s1.name.compareTo(s2.name);
    }
});

// Multiple criteria
Comparator<Student> comp = Comparator
    .comparingInt((Student s) -> s.rollNumber)
    .thenComparing(s -> s.name);
students.sort(comp);
```

### Comparison:

| Aspect | Comparable | Comparator |
|--------|---|---|
| Package | java.lang | java.util |
| Method | compareTo() | compare() |
| Implementation | Implement in class | Separate implementation |
| Criteria | Single (natural order) | Multiple possible |
| Flexibility | Fixed | Flexible (multiple comparators) |
| Use Case | One natural ordering | Multiple orderings needed |


