# 🧑‍🏫 Lab 7 — Packages & Inheritance


## 🗂️ 1. Java Packages

### 1. What is a Package?

A **package** in Java is like a **folder** that groups related classes together.

**Purpose:**
- Organize source code and avoid name conflicts.
- Make code easier to maintain and reuse.
- Control access between classes.

Example:  
`com.example.school` → means folders `com/example/school/`

---

### 2. Declaring a Package

At the top of your Java file, write:

```java
package com.example.school;
```
This line must be the first line in the file.

3. Example Project Structure
```java
project/
 ├── src/
 │    └── com/
 │        └── example/
 │            └── school/
 │                ├── Student.java
 │                └── Main.java
 └── bin/     ← compiled files will go here
```
* Step 1 — Compile:
```
cd project/src
javac -d ../bin com/example/school/*.java
```


✅ The -d ../bin option means:

Place the compiled .class files into the ../bin folder,
while keeping the same package folder structure.

* Step 2 — Run:
```
cd ../bin
java com.example.school.Main
```

### ➤ Importing Classes
You can use classes from other packages using the `import` statement.

Example with import

If you have another package:
```java
com/example/app/
 ├── Main.java
com/example/school/
 ├── Student.java
```
```java
package com.example.app;
import com.example.school.Student;

public class Main {
    public static void main(String[] args) {
        Student s = new Student("Bob");
        s.showInfo();
    }
}
```

> **Note:**  
> - The `package` statement must come **before** any `import` statements.  
> - Only **comments or blank lines** can come before `package`.

### CLASSPATH
####  1. What is the Classpath?

**Classpath** = the path (or location) where the **Java Virtual Machine (JVM)** and **compiler (`javac`)** look for `.class` files.

👉 It tells Java **where to find**:
- Your compiled classes
- Imported packages
- External libraries (like `.jar` files)

---

#### 2. Default Classpath

By default, Java uses the **current folder (`.`)** as the classpath.

So if you run:
```bash
java com.example.school.Main
```
Java starts searching for:
```
com/example/school/Main.class
```
### 3. using classpath -cp

If your compiled classes are in another folder (like ./bin),
and you are not inside that folder,
you must tell Java where to find them:
```
java -cp ./bin com.example.school.Main
```
---

