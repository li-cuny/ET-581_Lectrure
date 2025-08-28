# Aug 26 (Tue)

## Git Commands (Basic Workflow)

- **`git add .`** → stage all changes in the current directory  
- **`git add <file>`** → stage a specific file only  
- **`git commit -m "message"`** → commit staged changes with a descriptive message  
- **`git status`** → see current repository state (staged, unstaged, untracked files)  
- **`git push`** → send committed changes to your remote repository (e.g., GitHub)  
- **`git log`** → view commit history  

---

## Java Platforms (JVM, JRE, JDK)

### JVM – Java Virtual Machine
- Translate bytecode to machine code  

### JRE – Java Runtime Environment
- **JVM + core libraries (API)**  
- Can **run** Java programs  

### JDK – Java Development Kit
- **JRE + compiler + dev tools (javac, javadoc, etc.)**  
- Can **write, compile, and run** Java programs  

---

## First Java Program Basics

1. Must have a **class**  
2. **Class name should use PascalCase** (start with a capital letter)  
3. **Filename must match the public class name**  
4. Program execution **starts from `main` method:**
    ```java
    public static void main(String[] args)
    ```
5. **Compile first, then run:**
    ```bash
    javac FileName.java
    java FileName
    ```

### Minimal Example

Filename: HelloWorld.java
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
