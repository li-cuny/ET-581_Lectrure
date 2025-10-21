## private constructor
When a constructor is declared private, only the class itself can call it.
No other class (not even subclasses) can create its objects directly using new.

Example 1 — Restrict Object Creation
```java
class Example {
    private Example() {
        System.out.println("Private constructor called");
    }

    public static void showMessage() {
        System.out.println("Hello from static method");
    }
}

public class Main {
    public static void main(String[] args) {
        // Example e = new Example(); // ❌ Error: constructor is private
        Example.showMessage(); // ✅ Allowed
    }
}
```

Example 2 — Singleton 
A private constructor is often used to enforce that only one instance of a class can exist.
```
class Singleton {
    private static Singleton instance = new Singleton();

    private Singleton() {}  // Prevent direct instantiation

    public static Singleton getInstance() {
        return instance;
    }
}

public class Main {
    public static void main(String[] args) {
        Singleton s1 = Singleton.getInstance();
        Singleton s2 = Singleton.getInstance();
        System.out.println(s1 == s2); // true — same instance
    }
}
```

Sometimes you want exactly one shared resource in memory — for example:

- a single configuration manager

- a single database connection pool

- a single logging service

### static variable init locations

- Static variables → static block or declaration.
```java
class Test {
    static int x = 100; // init at declaration
    static int y;

    static {
        y = 100; // init inside of static block
    }
}
```

- Instance variables → declaration, instance block, or constructor.
```java
class Test {
    int x;
    int y;

    {
        x = 50; // init in instance block
        
    } 

    Test() {
        y = 10; // init in constructor
    }
    Test(int y) {
        this.y = y;
    }
}
```
instance block can be used **common initialization code for  multiple constructors**.
However in most of cases we are using
**constructor chaining** instead.

```java
class Test {
    int x, y;

    Test() {
        this(10);  // call parameterized constructor
    }

    Test(int y) {
        x = 50;     // common initialization
        this.y = y;
    }
}
```
#### Advantages of constructor chaining over instance blocks:

- Clearer: all initialization logic is inside constructors.

- Parameterizable: can pass values between constructors.

- Easier to read and maintain.




