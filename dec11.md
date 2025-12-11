# Enum
## 1. What is an Enum?

An **enum** (short for *enumeration*) is a special Java type used to define a **fixed set of constants**.

Examples:
- Days of the week: `MONDAY, TUESDAY, …`
- Directions: `NORTH, SOUTH, EAST, WEST`
- Traffic lights: `RED, YELLOW, GREEN`

> **Why use enums?**  
> They make your code **readable, type-safe, and maintainable**. You avoid using "magic numbers" or plain strings.

---

## 2. Basic Syntax

```java
// Define an enum
enum Day {
    MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}

// Using an enum
public class EnumExample {
    public static void main(String[] args) {
        Day today = Day.MONDAY;
        System.out.println("Today is: " + today);
    }
}
```
## 3. Switch statement
```java
Day today = Day.WEDNESDAY;

switch (today) {
    case MONDAY -> System.out.println("Start of the week!");
    case FRIDAY -> System.out.println("Almost weekend!");
    case SATURDAY, SUNDAY -> System.out.println("Weekend!");
    default -> System.out.println("Midweek...");
}
```
