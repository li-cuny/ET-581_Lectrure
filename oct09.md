## 1. Inheritance in Java

### ➤ Concept
- **Inheritance** allows one class to **reuse** the code of another.
- The class being inherited from is the **superclass**.
- The class that inherits is the **subclass**.

**Syntax:**
```java
class Parent {
    // Parent field and method
}
class Child extends Parent {
     // Child field and method
}
```


📊 **IS-A Relationship:**  
`Child IS-A Parent`

---

### ➤ Inherited Members
When a subclass is created using `extends`, it automatically gets most of the members (fields and methods) of its superclass, except some special cases.
| Member Type                     | Inherited?                 | Notes                                                                                                                |
| ------------------------------- | -------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| **Fields (instance variables)** | ✅ Yes                      | But access depends on the **access modifier** (e.g., `private` not directly accessible).                             |
| **Instance methods**            | ✅ Yes                      | Can be used or **overridden** in the subclass.                                                                       |
| **Private members**             | ✅ Yes,  but ⚠️ Not directly accessible | They exist in the object but are **hidden**; accessible only through **public methods** of the superclass. |
| **Constructors**                | ❌ No                       | Constructors are **never inherited**. A subclass must call one using `super()`.                                      |
```java
class Parent {
    public String a = "a";
    private String b = "b";
    public String getB(){
        return this.b;
    }
    private void doubleB(){
        this.b = this.b + this.b;
    }
}

class Child extends Parent {
    private String c = "c";
    public void print(){
        this.a; // visible
        this.b; // not visible
        this.getB(); // visible
        this.doubleB(); // not visible
    }
}
```
#### ➤ Constructor Calls and Inheritance
When you create a subclass object, the constructor of the parent class is always called first.

If you do not explicitly call a parent constructor using `super()`,
the compiler automatically inserts a call to the no-argument parent constructor (super();) as the first line of the subclass constructor.
```java
class Parent {
    Parent() {
        System.out.println("Parent constructor");
    }
}

class Child extends Parent {
    // No constructor explicitly written
}

public class Main {
    public static void main(String[] args) {
        Child c = new Child();
    }
}
```
even though Child has no constructor, Java automatically add
```java
Child() {
    super(); // automatically inserted
}
```
If the parent class does NOT have a no-argument constructor, and the subclass does not explicitly call super(args), you will get a compile-time error.
```java
class Parent {
    Parent(int x) { }
}

class Child extends Parent {
    // ❌ Compiler error: Parent() does not exist
}
```
---

## 2. Multiple Inheritance
- Java **does not support** multiple inheritance using classes to avoid ambiguity.

Example problem:
```java
class A { void show() {} }
class B { void show() {} }
class C extends A, B { }  // ❌ Error
```

Use **interfaces** for multiple inheritance (will be covered later).

---

## 🤝 3. Aggregation (HAS-A Relationship)
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


## 🔄 4. Method Overriding
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
#### ➤ Overloading VS. Overriding
**Overloading** → “Same name, different forms” → happens in **same class** → compile-time resolution

**Overriding** → “**Subclass**  `replaces` parent behavior” → happens across classes → runtime resolution


🧩 **Static methods cannot be overridden.**

---

## 🧬 5. Covariant Return Type
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

## 🧰 6. `super` Keyword
Used to refer to the **parent class**.

Examples:
```java
super.varName;         // Access parent variable
super.methodName();    // Call parent method
super();               // Call parent constructor
```

> The parent constructor runs **before** the child’s constructor.

---

## ⚙️ 7. Instance Initializer Block
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

