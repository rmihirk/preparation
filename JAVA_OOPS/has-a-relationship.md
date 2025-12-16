<em>

# HAS-A Relationship (Composition & Aggregation)

The HAS-A relationship is also known as Composition or Aggregation.

## Implementation
There is no specific keyword; it is implemented mostly by creating object references using the `new` operator.

## Advantage
Reusability (e.g., reuse the Engine logic within Car).

## Example

```java
class Car {
    Engine e = new Engine(); // Car HAS-A Engine reference
}
```

## Disadvantage
Increases dependency between the components and can create maintenance problems.

# Composition vs Aggregation (Association)

| Feature        | Composition (Strong Association / Dependent) | Aggregation (Weak Association / Independent) |
|----------------|----------------------------------------------|----------------------------------------------|
| **Existence**  | Contained object cannot exist without the container object. | Contained object can exist without the container object. |
| **Life Cycle** |Dependent. Contained objects are destroyed when the container object is. | Independent. Contained objects persist if the container object is destroyed. |
| **Example**    | University (Container) → Department (Contained) | Department (Container) → Professor (Contained) |
| **Reference**  | Container objects hold the contained object directly. | Container object holds only the reference of the contained object. |

</em>
