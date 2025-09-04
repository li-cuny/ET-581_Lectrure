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
public class ConcatExample {
    public static void main(String[] args) {
        String s1 = "Hello";
        String s2 = " World";
        String result = s1.concat(s2);
        System.out.println(result); // Output: Hello World
    }
}
```

---

## 2. `replace()`
**Definition:**
```java
String replace(char oldChar, char newChar)
```
- Replaces all occurrences of one character with another.

**Example:**
```java
public class ReplaceExample {
    public static void main(String[] args) {
        String text = "java";
        String result = text.replace('a', 'o');
        System.out.println(result); // Output: jovo
    }
}
```

---

## 3. `charAt()`
**Definition:**
```java
char charAt(int index)
```
- Returns the character at a specific index (starting at `0`).

**Example:**
```java
public class CharAtExample {
    public static void main(String[] args) {
        String word = "Java";
        char ch = word.charAt(2);
        System.out.println(ch); // Output: v
    }
}
```

---

## 4. `length()`
**Definition:**
```java
int length()
```
- Returns the number of characters in the string.

**Example:**
```java
public class LengthExample {
    public static void main(String[] args) {
        String text = "Programming";
        int len = text.length();
        System.out.println(len); // Output: 11
    }
}
```

**Full method list:** [Java String API](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html)

### How to Read a Method Definition

**Example 1:**

```java
String replace(char oldChar, char newChar)
```

* Method name: `replace`
* Return type: `String`
* Parameters:

  1. `oldChar` (type `char`) → character to replace
  2. `newChar` (type `char`) → character to replace with

**Example 2:**

```java
boolean methodName(int x, String y) {
    // method body
}
```

* Method name: `methodName`
* Return type: `boolean`
* Parameters:

  1. `x` (type `int`)
  2. `y` (type `String`)
* Method body: code inside `{ ... }` is executed when the method is called
