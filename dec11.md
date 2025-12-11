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
# Java Swing GUI

## 1. What is Swing?

- Swing is Java’s **GUI toolkit** for desktop applications.
- Provides **lightweight components** like buttons, labels, text fields, tables, and trees.

> Think of Swing as **LEGO for GUIs** — you assemble components to build interfaces.

---

## 2. Core Components

| Component       | Purpose                        |
|-----------------|--------------------------------|
| `JFrame`        | Main window                    |
| `JPanel`        | Container for grouping items   |
| `JButton`       | Clickable button               |
| `JLabel`        | Display text or images         |
| `JTextField`    | Single-line input              |
| `JTextArea`     | Multi-line input               |
| `JComboBox`     | Dropdown list                  |
| `JCheckBox` / `JRadioButton` | Selection options |

https://github.com/li-cuny/ET-581_Demo/blob/main/L14/Ex39_core_components/SwingCore.java

---

## 3. Event Handling

Swing is **event-driven**. Components react to user actions using listeners.

```java
JButton button = new JButton("Click Me");
button.addActionListener(e -> System.out.println("Button clicked!"));
```
## 4. Layout Manager
| Layout       | Diagram                          |
| ------------ | -------------------------------- |
| FlowLayout   | `[Btn1] [Btn2] [Btn3]`           |
| BorderLayout | `NORTH`<br>`CENTER`<br>`SOUTH`   |
| GridLayout   | `[Btn1][Btn2]`<br>`[Btn3][Btn4]` |

https://docs.oracle.com/javase/tutorial/uiswing/layout/visual.html
