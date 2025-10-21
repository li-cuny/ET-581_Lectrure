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

