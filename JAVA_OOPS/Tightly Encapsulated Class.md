Method Signature
In Java, the Method Signature consists of the name of the method followed by argument types.

Example: For public void m1(int i, float f);, the method signature is m1(int i, float f).

In Java, the return type is NOT part of the method signature.

The compiler will use the method signature while resolving method calls.

Important Note: Within the same class, we cannot take two methods with the same signature; otherwise, we will get a compile-time error.

Example (Compile-time Error):

Java

// Class Test
public void m1() {}
public int m1() { return 10; } // Compile-time error: Method m1() is already defined in Test