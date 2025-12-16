<em>

# Encapsulation

## Definition
Binding of data and corresponding methods into a single unit is called Encapsulation.

## Relation to Other Concepts
If any Java class follows data hiding and abstraction, such type of class is said to be an encapsulated class.

**Encapsulation = Data Hiding + Abstraction**

## Example: Class Account

```java
class Account {
    private double balance;

    // welcome to bank
    public double getBalance() {
        // validate user
        return balance;
    }

    public void setBalance(double balance) {
        // validate user
        this.balance = balance;
    }
}
```

- `getBalance()` - returns balance
- `setBalance()` - sets balance

## Advantages of Encapsulation

- Achieve security
- Enhancement becomes easy
- Improves maintainability and modularity of the application
- Provides flexibility for users to use the system easily

## Disadvantages of Encapsulation

- Increases code length
- Slows down execution

## Note
Every data member should be declared as `private`, and for every member, maintain getter and setter methods.

</em>
