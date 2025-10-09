## 🧱 2. Inheritance in Java

### ➤ Concept
- **Inheritance** allows one class to **reuse** the code of another.
- The class being inherited from is the **superclass**.
- The class that inherits is the **subclass**.

**Syntax:**
```java
class Parent {
    void show() { System.out.println("Parent class"); }
}

class Child extends Parent {
    void display() { System.out.println("Child class"); }
}
```

📊 **IS-A Relationship:**  
`Child IS-A Parent`

---

### ➤ Inherited Members
A subclass automatically gets:
- All **public** and **protected** fields/methods.
- **Private** members are *not directly inherited* but accessible via public methods.

---

## 🚫 3. Multiple Inheritance
- Java **does not support** multiple inheritance using classes to avoid ambiguity.

Example problem:
```java
class A { void show() {} }
class B { void show() {} }
class C extends A, B { }  // ❌ Error
```

Use **interfaces** for multiple inheritance (will be covered later).

---

## 🤝 4. Aggregation (HAS-A Relationship)
- When one class has a reference to another class.

Example:
```java
class Address {
    String city;
}

class Student {
    Address addr; // HAS-A relationship
}
```

Use **inheritance** for **IS-A**, and **aggregation** for **HAS-A**.

---

## 🔁 5. Method Overloading
- Same method name, **different parameters**.

Example:
```java
class MathTool {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
}
```
- Improves **readability** and **code reusability**.
- Overloading depends on:
  - Number of parameters
  - Type of parameters
- ❌ Return type alone cannot distinguish overloaded methods.

---

## 🔄 6. Method Overriding
- Same method name and parameters, but **different implementation** in subclass.

Example:
```java
class Animal {
    void sound() { System.out.println("Animal sound"); }
}
class Dog extends Animal {
    void sound() { System.out.println("Bark"); }
}
```

📘 **Rules:**
- Same name and parameters.
- Must be in a subclass (**IS-A** relationship).
- Used for **runtime polymorphism**.

🧩 **Static methods cannot be overridden.**

---

## 🧬 7. Covariant Return Type
- Since Java 5, subclass methods can override a parent method and return a **subtype**.

Example:
```java
class Animal {}
class Dog extends Animal {}

class AnimalShelter {
    Animal getAnimal() { return new Animal(); }
}

class DogShelter extends AnimalShelter {
    Dog getAnimal() { return new Dog(); }  // ✅ Covariant return type
}
```

---

## 🧰 8. `super` Keyword
Used to refer to the **parent class**.

Examples:
```java
super.varName;         // Access parent variable
super.methodName();    // Call parent method
super();               // Call parent constructor
```

> The parent constructor runs **before** the child’s constructor.

---

## ⚙️ 9. Instance Initializer Block
- Runs each time an object is created, **after the parent constructor**.

Example:
```java
class Demo {
    { System.out.println("Instance block"); }
}
```

---

## 🔒 10. The `final` Keyword
Used to **restrict modification**:
- `final class` → cannot be extended.
- `final method` → cannot be overridden.
- `final variable` → value cannot change.

Example:
```java
final class A {}
class B extends A {}   // ❌ Error
```

---

## 🧩 Summary

| Concept | Keyword | Relationship | Example |
|----------|----------|---------------|----------|
| Package | `package`, `import` | Folder-like grouping | `java.util` |
| Inheritance | `extends` | IS-A | `class Dog extends Animal` |
| Aggregation | reference field | HAS-A | `Student has Address` |
| Overloading | same name, diff params | compile-time | `add(int, int)` |
| Overriding | same name, same params | runtime | `sound()` |
| `super` | access parent | inheritance helper | `super.show()` |
| `final` | prevent change | restriction | `final class` |

---

## 💡 Practice Exercise
1. Create a package `school` and add a class `Student` with fields `name` and `grade`.
2. Create another class `CollegeStudent` in the same package that **inherits** from `Student`.
3. Add an overridden method `display()` to show extra info for college students.
4. Write a main program that imports the package and tests inheritance.

