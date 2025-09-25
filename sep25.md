# Java Lecture 5: Functions & Methods

## Methods / Functions
- A block of code executed when called.
- Benefits: code reuse.
- Must be defined inside a class.

### Syntax
```java
public class Main {
    static void myMethod() {
        // code
    }
}
```

### Parameters & Arguments
- Parameters → variables inside methods.  
- Arguments → values passed when calling.  

Example:
```java
static void greet(String name) {
    System.out.println("Hello " + name);
}
```

### Return Values
- Use a return type instead of `void`.  
```java
static int add(int a, int b) {
    return a + b;
}
```

### Method Overloading
having multiple methods with the `same name` but `different parameters` in the same class.

```java
int square(int x);
double square(double x);
```

⚠️ Key Notes

* Overloading methoed is determined at compile time.

* Return type alone cannot distinguish overloaded methods.
```java
static int add(int a, int b) {
    return a + b;
}
static double add(int a, int b) {
    return (double) a + b;
}
//error: method add(int,int) is already defined
```

---

## Scope
the part of a program where a variable is visible (can be accessed/used)
### 1. Class Scope (Global to the class)

Variables declared inside a class but outside methods/blocks.

Known as `fields` or `instance variables`.

Accessible by all methods in that class.
```java
class Example {
    int x = 10; // class scope (instance variable)

    void print() {
        System.out.println(x); // accessible here
    }
}
```

### 2. Method Scope (Local variables)

Variables declared inside a method.

- Exist only while the method runs.

- Not accessible from outside the method.
```java
class Example {
    void show() {
        int y = 20; // method scope
        System.out.println(y);
    }
    // System.out.println(y); ❌ ERROR (y not visible here)
}
```

### 3. Block Scope

Variables declared inside `{ }` (if, loop, etc.) are visible only in that block.
```java
class Example {
    void test() {
        if (true) {
            int z = 30; // block scope
            System.out.println(z);
        }
        // System.out.println(z); ❌ ERROR (z not visible outside the block)
    }
}
```
### 4. Loop Scope

A loop variable is accessible only within the loop.
```java
for (int i = 0; i < 5; i++) {
    System.out.println(i); // i is valid here
}
// System.out.println(i); ❌ ERROR
```
### 5. Parameter Scope

Method parameters are treated as local variables.
```java
void greet(String name) {
    System.out.println("Hello " + name); // name is valid only here
}
```

⚠️ Key Notes

* Java does not allow using a variable before declaration.

* Inner scope can shadow outer scope variables (same name → inner wins).
```java
int x = 10;
{
    int x = 20; // ❌ ERROR: cannot redeclare x in same scope
}
```

---

## Arrays & Method
- Pass single element: `arr[i]`  
```java
void doubleValue(int n) {
    n = n * 2; // only changes local copy
}
int[] numbers = {1, 2, 3};
doubleValue(numbers[0]);
```
- Pass entire array: `int[] arr`  
```java
void doubleValue(int[] arr) {
    arr[0] = arr[0] * 2; // modifies original array
}
int[] numbers = {1, 2, 3};
doubleValue(numbers);
```
- the array variable just hold a reference (address) of original array.

---

## Exercises 
  
* Power function 
* Dice roll simulation (1–6).  
* Array min & average (1D, 2D).  
