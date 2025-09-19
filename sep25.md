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
- Same method name, different parameter list.
```java
int square(int x);
double square(double x);
```

---

## Scope
- **Method scope**: variables only inside method.  
- **Block scope**: variables only inside `{}` block.  

---

## Arrays & Functions
- Pass element: `arr[i]`  
- Pass entire array: `int[] arr`  
- Arrays are reference types → methods can modify them.

---

## Exercises 
  
* Power function 
*  Dice roll simulation (1–6).  
*  Array min & average (1D, 2D).  


---

✅ **Focus**: Methods, parameters, return values, overloading, scope, arrays, and Math class usage.
