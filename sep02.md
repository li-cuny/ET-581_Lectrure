# Lecture Summary: Git and Java Object Creation

## 1. Git

* **Clone a repository:**

```
git clone <repo-URL>
```

* **Example:**

```
git clone https://github.com/user/project.git
```

---

## 2. Java: Object Creation

### Class Definition

```
class Car {
    // class body
}
```

### Creating Objects

```
Car car = new Car(); // create a Car object
Car car = new Car("Toyota"); // if class body/definition says there is a String param
```

### Creating Strings

* **Using new keyword:**

```
String str1 = new String("param");
```

* **Using literal (preferred):**

```
String str2 = "string";
```

**Note:** Using string literals is more efficient because they use the **String Constant Pool**.

### String Class Methods

## 1. `concat()`
**Definition:**
```java
String concat(String str)
```
- Joins the given string to the end of another string.

**Example:**
```java
String s1 = "Hello";
String s2 = " World";
String result = s1.concat(s2);  // result = "Hello World"
```

## 2. `replace()`
**Definition:**
```java
String replace(char oldChar, char newChar)
```
- Replaces all occurrences of one character with another.

**Example:**
```java
String text = "java";
String result = text.replace('a', 'o');  // result = "jovo"
```

## 3. `charAt()`
**Definition:**
```java
char charAt(int index)
```
- Returns the character at a specific index (starting at 0).

**Example:**
```java
String word = "Java";
char ch = word.charAt(2);  // ch = 'v'
```

## 4. `length()`
**Definition:**
```java
int length()
```
- Returns the number of characters in the string.

**Example:**
```java
String text = "Programming";
int len = text.length();  // len = 11
```

**Full method list:** [Java String API](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html)

### How to Read a Method Definition

```java
String replace(char oldChar, char newChar)
```

- Method name: `replace`
- Return type: `String`
- Parameters:
  1. `oldChar` (char)
  2. `newChar` (char)

```java
boolean methodName(int x, String y) {
    // method body
}
```

- Method name: `methodName`
- Return type: `boolean`
- Parameters:
  1. `x` (int)
  2. `y` (String)
- Method body: code inside `{ ... }`

### Invoking Methods
Class Definition
```java
class Car {
    void startEngine() {
        System.out.println("Engine started!");
    }
}
```

Invoking method using dot(`.`) follwed by methodName();
```java
Car myCar = new Car();   // create object
myCar.startEngine();     // invoke the method
```