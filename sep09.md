# Loops in Java

## 1. While Loop
- A **while loop** repeats a block of code **as long as a condition is true**.

### Syntax:
```java
while (condition) {
    // code block to be executed
}
```

### Example 1: Asking for a Password
**Scenario:** Keep asking the user until the password is valid.  
- **Condition:** `password is not valid`  
- **Action:** Ask user to enter password again

```java
while (!isPasswordValid) {
    System.out.print("Enter password: ");
    password = scanner.nextLine();
}
```

### Example 2: Printing Numbers Less Than 5
```java
int num = 0;
while (num < 5) {
    System.out.println(num);
    num++;
}
```

### Pseudocode for While Loop
```
LOOP_START:
    if (condition not true) jump to LOOP_END
    // code block to be executed
    jump to LOOP_START
LOOP_END:
```

---

## 2. Do...While Loop
- Executes the loop **body first**, then checks the condition.  
- This ensures the loop runs **at least once**.

### Syntax:
```java
do {
    // code block to be executed
} while (condition);
```

### Pseudocode:
```
LOOP_START:
    // code block to be executed
    if (condition true) jump to LOOP_START
LOOP_END:
```

---

## 3. For Loop
- A **for loop** is a simpler way to handle loops with:  
  - **Initialization**  
  - **Condition**  
  - **Update**

### While Loop Equivalent
```java
int i = 0;                  // initialization
while (i < 5) {             // condition
    System.out.println("i = " + i);
    i++;                    // update
}
```

### Simplified For Loop
```java
for (int i = 0; i < 5; i++) {
    System.out.println("i = " + i);
}
```

### Why Use a For Loop?
1. **Easy to read and shorter** → all in one line  
2. **Prevent mistakes** → less chance of forgetting the update (`i++`)  
3. **Intent is clear**  
   - `for` → repeat a fixed number of times  
   - `while` → repeat until a condition becomes false (not necessarily a fixed count)

---

## 4. Break
- **Purpose:** Exit the loop immediately, regardless of the condition.  
- Think of it as **“break out of the loop.”**

### Example:
```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break; // stop the loop entirely
    }
    System.out.println("i = " + i);
}
```

**Output:**
```
1
2
3
4
```

---

## 5. Continue
- **Purpose:** Skip the **current iteration** and move to the next one.  
- Think of it as **“continue to the next round.”**

### Example:
```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue; // skip printing 3
    }
    System.out.println("i = " + i);
}
```

**Output:**
```
1
2
4
5
```

### Key Difference
- `break` → jumps **out of the loop**  
- `continue` → jumps to **loop update** (`i++`) and then back to the start

