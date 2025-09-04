# Lecture Summary: Java Basics with Examples

## 1. Comparison Operators

| Operator | Description           | Example                   |
|----------|----------------------|---------------------------|
| `==`     | Equal to             | `5 == 5` → true          |
| `!=`     | Not equal to         | `5 != 3` → true          |
| `>`      | Greater than         | `5 > 3` → true           |
| `<`      | Less than            | `5 < 3` → false          |
| `>=`     | Greater than or equal| `5 >= 5` → true          |
| `<=`     | Less than or equal   | `5 <= 6` → true          |

**Compare numbers:**
```java
int a = 10, b = 20;
System.out.println(a < b); // true
```

**Compare Strings:**
```java
String s1 = "Hello";
String s2 = "World";
System.out.println(s1.equals(s2)); // false
```

---

## 2. String Methods

- `.equals()` : Check if two strings are the same
```java
String str1 = "Java";
String str2 = "Java";
System.out.println(str1.equals(str2)); // true
```

- `.compareTo()` : Lexicographic comparison (used for sorting)
```java
String str1 = "apple";
String str2 = "banana";
System.out.println(str1.compareTo(str2)); // negative number (apple < banana)
System.out.println(str2.compareTo(str1)); // positive number (banana > apple)
```
- `.indexOf(String s)` : first occurrence of the specified string
- `.substring(int index)` : return  substring index to end
```java
 String sentence = "Hello world Java";
 int index = sentence.indexOf("world");
 System.out.println(sentence.substring(index));
 //output:world Java
```
---

## 3. Logical Operators

- `&&` : AND  
- `||` : OR  
- `!`  : NOT  

**Example:**
```java
boolean a = true;
boolean b = false;

System.out.println(a && b); // false
System.out.println(a || b); // true
System.out.println(!a);     // false
```

---

## 4. Conditional Statements

### if
**if (condition) statement;** // or **blocks** `{...}` which is group of statements;
```java
int number = 2;
if (number % 2 == 0) {
    System.out.println("Even number");
} else {
    System.out.println("Odd number");
}
```
### ternary operator 

**variable = (condition) ? valueIfconditionTrue : valueIfconditionFalse;**
```java
int number = 2;
boolean isNumberEven = (number % 2 == 0) ? true: false;
```



### switch
```java
int day = 2;

switch(day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    default:
        System.out.println("Other day");
}
// Output: Tuesday
```
 ## StringTokenizer
- `"Hello world Java"` — how can we separate each word?
- `StringTokenizer` breaks a string into smaller parts (tokens) using **delimiters** (default: space " ")
```java
import java.util.StringTokenizer;

String sentence = "Hello world Java";
StringTokenizer st = new StringTokenizer(sentence);// default delimiter " " space
System.out.println(st.nextToken()); // Hello

String data = "apple,banana,orange";
StringTokenizer st = new StringTokenizer(data, ","); // using "," as separator
System.out.println(st.nextToken()); // apple
```