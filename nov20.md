# Generics

Generics allow classes, interfaces, and methods to operate on **different data types** while still providing **type safety** and **code reuse**. This becomes especially important when creating your own custom classes.

---

## 1. Reusability for Any Data Type
Without generics, a custom class that stores data typically uses `Object`:

```java
class Box {
    private Object value;
    public void setValue(Object value) { this.value = value; }
    public Object getValue() { return value; }
}
```

This design works, but has limitations:
- Requires **casting** when retrieving values
- **No type restriction**, so incorrect types can be inserted

Using generics makes the class reusable for any type:

```java
class Box<T> {
    private T value;
    public void setValue(T value) { this.value = value; }
    public T getValue() { return value; }
}
```

Now you can use:

```java
Box<String> sBox = new Box<>();
Box<Integer> iBox = new Box<>();
Box<User> uBox = new Box<>();
```

---

## 2. Eliminates Multiple Class Versions
Without generics, you might end up writing several classes:

- `IntBox`
- `StringBox`
- `UserBox`

Generics replace all of these with a single, flexible class:

```java
Box<T>
```

---

## 3. Type Safety
Generics enforce the correct type at **compile time**.

```java
Box<String> box = new Box<>();
box.setValue(10); // Compile-time error
```

Without generics:

```java
Box box = new Box();
box.setValue("Hello");
box.setValue(100); // Allowed, unsafe

String s = (String) box.getValue(); // Runtime error
```

Generics prevent these issues early.

---

## 4. No Need for Casting
Without generics:

```java
String s = (String) box.getValue();
```

With generics:

```java
String s = box.getValue();
```

Cleaner, safer, easier.

---

## 5. Consistency With Java Collections
Java's built-in classes already use generics:

- `ArrayList<E>`
- `HashMap<K, V>`
- `HashSet<E>`

Writing your custom classes with generics makes them behave the same way, providing:
- Familiar usage
- Better integration
- Modern code style

---
