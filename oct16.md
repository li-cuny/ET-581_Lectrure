# 📝 Lecture 8 

---
## 1. Polymorphism

### **Definition**

- **Polymorphism** = “many forms”  
- Occurs when **classes are related via inheritance**  
- Enables a **single action** to behave differently for different objects  
- Derived from Greek: *poly* = many, *morphs* = forms  

---

### **Types of Polymorphism**

#### 🧩 Compile-time Polymorphism (Static Polymorphism)
- Achieved via **method overloading**
- Example: Overloading a static method

#### ⚙️ Runtime Polymorphism (Dynamic Polymorphism)
- Achieved via **method overriding**
- Determined **at runtime**
- **Data members cannot be overridden** → runtime polymorphism only applies to methods

---

## 2. Runtime Polymorphism (Dynamic Method Dispatch)

When a **superclass reference variable** refers to a **subclass object**, it is called **upcasting**.  
The overridden method that gets called is determined by the **actual object type** at runtime.

### **Example**
```java
class Parent {
    void show() { System.out.println("Parent"); }
}

class Child extends Parent {
    void show() { System.out.println("Child"); }
}

public class Main {
    public static void main(String[] args) {
        Parent p = new Child(); // upcasting
        p.show(); // Output: Child → dynamic method dispatch
    }
}
```

---
## 3. Binding 

### 1. Field binding

* **Field access is compile-time bound**

* **No polymorphism for fields.**

* **just based on reference type** 
```java
class Parent { int x = 10; }
class Child extends Parent { int x = 20; }

Parent p = new Child();
System.out.println(p.x); // Output: 10 → field access based on reference type
```
### 2. Method binding
* Method calls can be runtime bound if the method is `overridden`
* determined by the `actual object type`.
* runtime polymorphism
```java
class Parent {
    void show() { System.out.println("Parent"); }
}

class Child extends Parent {
    void show() { System.out.println("Child"); }
}

public class Main {
    public static void main(String[] args) {
        Parent p = new Child();
        p.show(); // prints "Child"
    }
}
```

| **Binding Type** | **When Determined** | **Notes** |
|------------------|---------------------|------------|
| Static Binding (Early Binding) | Compile-time |  field access, private method, final method, and static methods |
| Dynamic Binding (Late Binding) | Runtime | Overridden instance methods |

---

---

## 4. `instanceof` Operator

- Tests whether an object is an **instance** of a class, subclass, or interface  
- Returns **true** or **false**
- If object is null, it always returns false.

### **Example**
```java
Parent p = new Child();
System.out.println(p instanceof Child);  // true
System.out.println(p instanceof Parent); // true
System.out.println(null instanceof Parent); // false
```

#### 5. Upcasting vs Downcasting

##### Upcasting
* Upcasting is casting a subclass object to a superclass reference.

* Always safe; no explicit cast is needed.
```java
class Parent {
    void show() { System.out.println("Parent show"); }
}

class Child extends Parent {
    void show() { System.out.println("Child show"); }
    void play() { System.out.println("Child play"); }
}

public class Main {
    public static void main(String[] args) {
        Parent p = new Child(); // Upcasting (automatic)
        p.show(); // Child show → runtime polymorphism
        // p.play(); // ❌ Compile-time error: Parent reference can't see Child-only methods
    }
}
```
##### Downcasting
* Downcasting is casting a superclass reference to a subclass reference.

* Explicit cast is required.

* Only safe if the actual object is really a Child; otherwise, runtime exception occurs (ClassCastException).

```java

// unsafe casting
Parent p2 = new Parent();
Child c2 = (Child) p2; // ❌ ClassCastException at runtime
// safe casting
Parent p = new Child();
if (p instanceof Child) {
    Child c = (Child) p;
    c.play();
}
```
```java
Heap:
[ Child object ]
 ├── Parent fields
 ├── Child fields
 └── class pointer → Child.class (Method Area)

Reference variable:
p ---> points to Child object
c ---> points to same Child object
```
---


### 6. Access Modifiers:

---

#### 1️⃣ Default Access(Package-Private Access) 

- No modifier written (just leave it blank)
- Accessible **only within the same package**
- Not accessible from subclasses in **different packages**

#### **Example**

##### File: `package1/Parent.java`
```java
package package1;

class Parent {          // default access
    int data = 100;     // default access
}
```

##### File: `package1/Main.java`
```java
package package1;

public class Main {
    public static void main(String[] args) {
        Parent p = new Parent();
        System.out.println(p.data); // ✅ Accessible (same package)
    }
}
```

##### File: `package2/Other.java`
```java
package package2;
import package1.Parent;

public class Other {
    public static void main(String[] args) {
        Parent p = new Parent(); 
        System.out.println(p.data); // ❌ Compile-time error (different package)
    }
}
```

---

#### 2️⃣ Protected Access

- Accessible **within the same package** (like default)
- Also accessible in **subclasses**, even in **different packages**

### **Example**

#### File: `package1/Parent.java`
```java
package package1;

public class Parent {
    protected int data = 100;
}
```

#### File: `package2/Child.java`
```java
package package2;
import package1.Parent;

public class Child extends Parent {
    public void showData() {
        System.out.println(data); // ✅ Accessible (protected)
    }
}

public class Main {
    public static void main(String[] args) {
        Child c = new Child();
        c.showData(); // Output: 100
    }
}
```

## 7. Nested / Inner Classes

### **Purpose**
Group related classes to improve **readability** and **maintainability**.

### **Accessing Inner Class**
```java
Outer outer = new Outer();
Outer.Inner inner = outer.new Inner();
```

---

### **Types of Inner Classes**

#### 1. Private Inner Class
- Not accessible from outside the outer class.

#### 2. Static Inner Class
- Can be accessed **without creating** an outer class object.

```java
Outer.StaticInner inner = new Outer.StaticInner();
```

✅ **Advantage:** Inner classes can access outer class **attributes and methods**, even if they are `private`.

* **Note**:A top-level class (not nested inside another class) cannot be static.
    ```java
    static class Parent {  
        // ❌ Compile-time error
    }
    ```
---

#### ✅ Key Points

- Runtime polymorphism works **only for methods**, not fields.  
- `static`, `private`, and `final` methods → **compile-time (static) binding**.  
- `instanceof` returns **false** for `null`.  
- **Upcasting:** `Parent p = new Child();`  
- Accessing inner classes:  
  - **Non-static:** needs outer object  
  - **Static:** no outer object needed  
- Overridden method execution is determined by the **actual object type**, not reference type.  
- Compile-time polymorphism → **method overloading**  
- Runtime polymorphism → **method overriding**
- `protected` → accessible in **same package + subclasses in other packages**  
- `default` → accessible **only in same package**  
- `private` → accessible **only within the same class**  
- `public` → accessible **everywhere**
