<em>
  
# Java Collections & Framework README

## Q1 What is a framework in Java?
A framework is a reusable, prebuilt architecture that provides a set of classes and interfaces to simplify development by offering common functionality and design patterns.

## Q2 What is the Collection framework in Java?
The Java Collection Framework is a set of interfaces and classes used to store and manipulate groups of objects. It includes implementations like `ArrayList`, `Vector`, `HashSet`, `Stack`, and interfaces such as `List`, `Set`, and `Queue`.

## Q3 Describe the Collection hierarchy in Java

<img width="917" height="517" alt="image" src="https://github.com/user-attachments/assets/aa379369-bc1e-4565-8b91-48cc1ea2c1f5" />

Key notes:
- `Collection` is the root interface for most collection types (except `Map`).
- `List` maintains insertion order and allows duplicates.
- `Set` enforces uniqueness; may not preserve order (except `TreeSet` and `LinkedHashSet`).
- `Queue` follows FIFO or priority-based ordering.
- `Map` stores key-value pairs independently from the `Collection` hierarchy.

## Java Collections Comparison Table

| Collection               | Ordering | Random Access | Key-Value | Duplicate Elements | Null Element | Thread Safety |
|--------------------------|----------|----------------|-----------|---------------------|---------------|----------------|
| ArrayList                | Yes      | Yes            | No        | Yes                 | Yes           | No             |
| LinkedList               | Yes      | No             | No        | Yes                 | Yes           | No             |
| HashSet                  | No       | No             | No        | No                  | Yes           | No             |
| TreeSet                  | Yes      | No             | No        | No                  | No            | No             |
| HashMap                  | No       | No             | Yes       | Yes                 | Yes           | No             |
| TreeMap                  | Yes      | No             | Yes       | Yes                 | No            | No             |
| Vector                   | Yes      | Yes            | No        | Yes                 | Yes           | Yes            |
| Hashtable                | No       | No             | Yes       | Yes                 | No            | Yes            |
| Properties               | No       | No             | Yes       | Yes                 | No            | Yes            |
| Stack                    | Yes      | No             | No        | Yes                 | Yes           | Yes            |
| CopyOnWriteArrayList     | Yes      | Yes            | No        | Yes                 | Yes           | Yes            |
| ConcurrentHashMap        | No       | No             | Yes       | Yes                 | No            | Yes            |
| CopyOnWriteArraySet      | No       | No             | No        | No                  | Yes           | Yes            |


## Q4 Primary interfaces provided by Java Collections Framework
- `interface Collection<E> extends Iterable<E>`  
  Root of the collection hierarchy; most collection classes implement this.

- `interface List<E> extends Collection<E>`  
  Ordered collection (insertion order), allows duplicates, index-based access. Implementations: `ArrayList`, `LinkedList`, `Vector`, `Stack`.

- `interface Set<E> extends Collection<E>`  
  No duplicate elements; no guaranteed order. Implementations: `HashSet`, `TreeSet`, `LinkedHashSet`.

- `interface Queue<E> extends Collection<E>`  
  Typically FIFO ordering (add at rear, remove from front); used for queuing.

- `interface Map<K, V>`  
  Key-value pairs (keys unique). Implementations: `HashMap`, `TreeMap`, `LinkedHashMap`.

## Q5 Why Collection doesn't extend Cloneable and Serializable?
Concrete implementations have different requirements for cloning and serialization. Leaving these out of `Collection` lets each implementation decide whether and how to support cloning or serialization.

## Q6 Major advantages of generic collections
- Stronger compile-time type checking  
- Eliminates need for explicit casts  
- Enables generic algorithms and cleaner, type-safe code

## Q7 Main benefit of using a properties file
Properties files allow configuration values (e.g., credentials, URLs) to be changed without recompiling code. Example:

```java
import java.util.*;
import java.io.*;

public class PropertiesDemo {
    public static void main(String[] args) throws Exception {
        FileReader fr = new FileReader("db.properties");
        Properties pr = new Properties();
        pr.load(fr);
        System.out.println(pr.getProperty("user"));
        System.out.println(pr.getProperty("password"));
        fr.close();
    }
}
```

## Q8 What is Iterator in the Java Collection Framework?
`Iterator` is a cursor-like interface to traverse collection elements one by one. It works with all `Collection` implementations and supports read and remove operations.

Key behaviors:
- Traverse elements sequentially  
- Universal cursor for collections  
- Supports `remove()` while iterating

## Q9 Why override equals()?
The default `equals()` checks reference equality. Override `equals()` to compare objects by meaningful properties (logical equality) rather than by identity.

## Q10 How the Collection objects are sorted in Java?
Sorting uses:
- `Comparable` (implement `compareTo()` for natural order) used by `Collections.sort(list)`
- `Comparator` (implement `compare()` to define custom order) used by `Collections.sort(list, comparator)`

## Q11 What is the use of the List interface?
`List` is an ordered collection that preserves insertion order and allows duplicates. It supports indexed access and positional manipulation. Main implementations: `ArrayList`, `LinkedList`, `Stack`, `Vector`.

## Q12 What is ArrayList in Java?
`ArrayList` is a resizable array implementation of `List` that allows dynamic addition/removal, positional access, and duplicates. Example declaration:

```java
ArrayList<Object> object = new ArrayList<>();
```

## Q13 How to convert between Array and ArrayList?
- Array → ArrayList:
  - Use `Arrays.asList(array)` to create a fixed-size `List` backed by the array.
  - To get a mutable `ArrayList`: `new ArrayList<>(Arrays.asList(array))`

- ArrayList → Array:
  - Use `toArray(T[] a)` e.g. `list.toArray(new String[list.size()]);`

## Q14 How to reverse a List?
Use `Collections.reverse(list)`.

Example:

```java
import java.util.*;

public class ReversingArrayList {
    public static void main(String[] args) {
        List<String> myList = new ArrayList<>();
        myList.add("AWS");
        myList.add("Java");
        myList.add("Python");
        myList.add("Blockchain");

        System.out.println("Before Reversing");
        System.out.println(myList);

        Collections.reverse(myList);

        System.out.println("After Reversing");
        System.out.println(myList);
    }
}
```

</em>
