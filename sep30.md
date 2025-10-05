## Classes & Objects

## 1. What is a Class?
- A **class** is a **blueprint** for creating objects.  
- It defines **fields (variables)** and **methods (functions)**.  

**Example:**
```java
class Car {
    String color;
    int year;

    void drive() {
        System.out.println("The " + color + year + " car is driving");
    }
}
```

---

## 2. What is an Object?
- An **object** is an **instance of a class**.  
- Created using the `new` keyword.  

**Example:**
```java
public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();   // object creation
        myCar.color = "Red";
        myCar.year = 2020;

        System.out.println(myCar.color); // prints "Red"
        myCar.drive();                   // calls method
    }
}
```
### Method Area

* Stores class bytecode and method code (drive()).

* Shared by all Car objects.
```java
Method Area:
 └─ Class: Car
     └─ Method: drive()
```
### Heap

* Stores object instances with their instance fields.
```java
Heap:
 └─ Object#1: Car (myCar)
      ├─ color → "Red"
      └─ year  → 2020
```
### Stack

* Stores local variables and method call frames.
```java
Stack:
 └─ main() frame
     ├─ local variable: myCar → reference to Object#1

 └─ drive() frame (when myCar.drive() is called)
     ├─ hidden parameter: this → Object#1
```
---
### Multiple Objects 
```java
Car car1 = new Car();   // object creation
        car1.color = "Red";
        car1.year = 2020;
     Car car2 = new Car();  
       car2.color = "Blue";
        car2.year = 2021;
        car1.drive();
        car2.drive();

```


#### Key Points
- **Class = Blueprint**  
- **Object = Instance of a class**  
- **Fields = Variables inside a class**  
- **Methods = Functions inside a class**  
- **Constructor = Special method for initialization**  

---



### Exercise 1
Create a `Student` class with:
- Fields: `name`, `age`
- Method: `study()` that prints `"Student is studying"`

Create 2 student objects and call their methods.

---

### Exercise 2
Add a **constructor** to `Student` to initialize `name` and `age` when creating objects.

---

### Exercise 3
Write a `Book` class with:
- Fields: `title`, `author`, `price`
- Constructor to initialize them
- Method `printDetails()` that prints info about the book  

Create 3 book objects and call their method.  

------------------------------------

## 3. Constructors
- A **constructor** is a special method that runs when an object is created.  
- Used to initialize fields.  
### Default Constructor Example

``` java
class Student {
    String name;
    int id;

    Student() {
        name = "Unknown";
        id = 0;
    }
}

public class Main {
    public static void main(String[] args) {
        Student s = new Student();
        System.out.println(s.name + " " + s.id); // Unknown 0
    }
}
```

### Parameterized Constructor Example

``` java
class Student {
    String name;
    int id;

    Student(String n, int i) {
        name = n;
        id = i;
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Alice", 101);
        Student s2 = new Student("Bob", 102);
        System.out.println(s1.name + " " + s1.id); // Alice 101
        System.out.println(s2.name + " " + s2.id); // Bob 102
    }
}
```

------------------------------------------------------------------------

## 4. Constructor Overloading

``` java
class Box {
    int length, width;

    // no-argument constructor
    Box() {
        length = 1;
        width = 1;
    }

    // parameterized constructor
    Box(int l, int w) {
        length = l;
        width = w;
    }

    int area() {
        return length * width;
    }
}

public class Main {
    public static void main(String[] args) {
        Box b1 = new Box();
        Box b2 = new Box(5, 10);

        System.out.println("Area b1 = " + b1.area()); // 1
        System.out.println("Area b2 = " + b2.area()); // 50
    }
}
```

------------------------------------------------------------------------

## 5. Encapsulation (Getters & Setters)
* **Getter**: A method that returns the value of a private field.

* **Setter**: A method that sets or updates the value of a private field.

They are used to encapsulate data, allowing controlled access to `private fields` from `other` classes.

``` java
class Account {
    private double balance; // access to private variable

    // Getter
    public double getBalance() {
        return balance;
    }

    // Setter
    public void setBalance(double balance) {
        this.balance = balance; 
    }
}

public class Main {
    public static void main(String[] args) {
        Account acc = new Account();
        acc.setBalance(1000);
        System.out.println("Balance: " + acc.getBalance()); // 500
    }
}
```

------------------------------------------------------------------------

## 6. `this` Keyword
The `this` keyword in Java is a reference variable that refers to the current object — the object whose method or constructor is being executed.
static method can be called without creating an object, there is no `“current object”` for `this` to refer to.

``` java
class Employee {
    String name;
    int salary;

    Employee(String name, int salary) {
        this.name = name;       // disambiguates parameter vs field
        this.salary = salary;
    }

    void display() {
        System.out.println(name + " earns $" + salary);
    }
}

public class Main {
    public static void main(String[] args) {
        Employee e1 = new Employee("John", 5000);
        e1.display(); // John earns $5000
    }
}
```

------------------------------------------------------------------------

## 7. Static vs Non-Static
* The `static` keyword belongs to the class, not to instances (objects).

* Static members (variables or methods) are shared among all objects of the class.

* You can access static members without creating an object.

``` java
class Counter {
    static int count = 0; // shared among all objects
    int id;

    Counter() {
        count++;
        id = count;
    }
}

public class Main {
    public static void main(String[] args) {
        Counter c1 = new Counter();
        Counter c2 = new Counter();
        Counter c3 = new Counter();
        System.out.println("c1 id = " + c1.id); // 1
        System.out.println("c2 id = " + c2.id); // 2
        System.out.println("Total objects = " + Counter.count); // 3
    }
}
```


## 8. Static Block

- Runs **only once** — when the class is loaded.
- Executed **before `main()`** or **before any object of the class is created**.
- **Cannot access instance variables** or use `this` — there is no object context.
- Can access **static variables** and call **static methods**.
- A class can have **multiple static blocks**, executed in the **order they appear**.

**Example:**
```java
class Car {
    static {
        System.out.println("Static block is invoked");
    }
    // only once when class loaed - class level
}
```

---

## 9. Instance Block

- An **instance block** (also called an **initializer block**) is a block of code inside a class **without the `static` keyword**.
- Runs **every time an object is created**, **before the constructor**.
- Can access **instance variables** directly.

**Example:**
```java
class Car {
    {
        System.out.println("Instance block is invoked");
    } // every time object created - obj level
}
```

## 10. Wrapper Classes

``` java
public class Main {
    public static void main(String[] args) {
        int primitive = 10;

        // Boxing (int → Integer)
        Integer obj = Integer.valueOf(primitive);

        // Unboxing (Integer → int)
        int value = obj.intValue();

        // Using utility methods
        int num = Integer.parseInt("123");

        System.out.println(obj);   // 10
        System.out.println(value); // 10
        System.out.println(num);   // 123
    }
}
```
------------------------------------------------------------------------
