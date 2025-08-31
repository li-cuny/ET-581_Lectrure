# Aug28

## 1. Git

- `git pull` --- update local repo from remote  
- `git log` --- view commit history

## 2. Comments

- `//` single-line  
- `/* ... */` multi-line

## 3. Variables and Data Types

- Declare variables before use: `type name = value;`  
- **Naming rules:**
  - Start with letter / `_` / `$`  
  - Case-sensitive  
  - Cannot use Java keywords  
  - CamelCase is common in practice  
- **Primitive types:**
  - `int`, `short`, `long` (whole numbers)  
  - `float`, `double` (decimals)  
  - `char` (single Unicode character)  
  - `boolean` (true/false)  
  - `byte` (range -128 to 127; often used for file or raw data handling)
- **Non-primitive types:** Strings, Arrays, Objects  
- **String vs char:** `"Hello"` vs `'H'`  

## 4. Arithmetic and Operators

- Operators: `+ - * / % ++ -- ()`  
- **Integer division** truncates decimals; **double division** keeps decimals  
- `%` modulus gives remainder  
- Floating-point calculations are **not exact** → use `BigDecimal` for precision when needed  

## 5. Type Casting

- **Widening (automatic):** small → large type (`int → double`)  
- **Narrowing (manual):** large → small type using `(type)`

```java
int i = 9;
double d = i;        // widening
int n = (int) d;     // narrowing
```

## 6. Input with Scanner

-   Import and use:

``` java
import java.util.Scanner;
Scanner input = new Scanner(System.in);
int x = input.nextInt();
input.close();
```

-   Methods: `nextInt()`, `nextDouble()`, `nextFloat()`, `nextLine()`,
    `next()`

## 7. Output Formatting (Not yet covered)

-   `System.out.println()` for simple output
-   `System.out.printf()` for formatted output:
    -   `%d` for integers
    -   `%.3f` for floating-point rounded to 3 decimals
