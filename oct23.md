# 🧾 Lecture 9 — Abstract Classes and Interfaces
---

## Abstraction

Abstraction in Java is the process of **hiding implementation details** and showing only essential features of an object.
- Abstraction = “Show only what is necessary, hide the rest.”
- Example: When you drive a car, you press the brake pedal — you don’t need to know how the hydraulic system works inside.
- Achieved using **abstract classes** or **interfaces**.

---

## 1. Abstract Class

### 🔹 What is an Abstract Class?
- A class declared with the **`abstract`** keyword.  
- **Cannot be instantiated** (no direct object creation).  
- Can include:
  - **Abstract methods** (no body)
  - **Non-abstract methods** (with body)
  - **Constructors**
  - **Static methods**
  - **Final methods** (cannot be overridden)

```java
abstract class Shape {
    abstract void draw();  // abstract method
    void info() {          // non-abstract method
        System.out.println("This is a shape.");
    }
}
```

---

### 🔹 Abstract Methods
- Declared **without a body**.  
- Must be **implemented by subclasses**.  
- The containing class must be **abstract**.

```java
abstract void printStatus(); // no method body
```

### 🔹 Rules
1. If a class has any abstract method, it **must be declared abstract**.  
2. A subclass extending an abstract class must either:
   - Implement all abstract methods, **or**
   - Be declared abstract itself.

---

### 🔹 Why & When to Use Abstract Classes
- To achieve **security** by hiding implementation details.  
- When you want to **share code among related classes**.  
- When you want to **define a common template** for subclasses.

---

## 2. Interface in Java

### 🔹 What is an Interface?
- A **completely abstract class** used to group related methods with empty bodies.  
- Declared using the **`interface`** keyword.

```java
interface Drawable {
    void draw();
}
```
Interface:
- Cannot be instantiated.  
- Methods are **implicitly**:
  - `public`
  - `abstract`
- Fields are **implicitly**:
  - `public`
  - `static`
  - `final`
- **No constructors** (interfaces cannot create objects).

---

### 🔹 Implementing an Interface

```java
interface Drawable {
    void draw();
}

class Circle implements Drawable {
    public void draw() {
        System.out.println("Drawing a circle");
    }
}
```

- Use the **`implements`** keyword.  
- The implementing class must **override all interface methods**.

---

### 🔹 Why Use Interfaces?
- To achieve **abstraction**.  
- To support **multiple inheritance** (since classes cannot extend multiple superclasses).  
- To achieve **loose coupling** and flexibility.

---

### 🔹 Multiple Interfaces

```java
interface A { void methodA(); }
interface B { void methodB(); }

class MyClass implements A, B {
    public void methodA() { System.out.println("A"); }
    public void methodB() { System.out.println("B"); }
}
```

✅ Supported in interfaces (unlike classes).  
✅ No ambiguity because **implementation is provided by the class**.

---

### 🔹 Extending Interfaces
- One interface can **extend another** (or multiple others):

```java
interface A { void a(); }
interface B extends A { void b(); }
```

---

### 🔹 Default & Static Methods in Interfaces

- **Default method:** Can have a body (introduced in Java 8).  
- **Static method:** Can have a body but cannot be overridden.

```java
interface Vehicle {
    default void start() {
        System.out.println("Vehicle starting...");
    }

    static void info() {
        System.out.println("All vehicles have wheels.");
    }
}
```

---

## ⚖️ Comparison: Abstract Class vs Interface

| Feature | Abstract Class | Interface |
|----------|----------------|-----------|
| Keyword | `abstract class` | `interface` |
| Object creation | ❌ Cannot instantiate | ❌ Cannot instantiate |
| Methods | Abstract + Non-abstract | Abstract (by default) + default/static |
| Variables | Any type | Always `public static final` |
| Multiple inheritance | Not supported | Supported |
| Constructors | ✅ Yes | ❌ No |
| Access Modifiers | Can be any | Always `public` |
| Use Case | Common base for related classes | Define contract for unrelated classes |

---
