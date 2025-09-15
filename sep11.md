# Java Arrays - Key Points

## 1. What is an Array?
A data structure that stores a fixed number of elements of the same type, accessible by an index.

**Key Points**
- **Same type**: All elements must be of the same data type (e.g., all `int`, all `String`).
- **Fixed size**: Once created, the length of the array cannot change.
- **Indexed**: Each element is identified by a position number (index), starting at 0.
- **Contiguous memory**: Elements are stored next to each other in memory.

```java
int[] numbers = {10, 20, 30, 40};
System.out.println(numbers[0]); // prints 10
System.out.println(numbers[3]); // prints 40
```

---

## 2. Declaration & Creation

**Declare only (no size, no values yet):**
```java
int[] numbers;   // Preferred style
int numbers[];   // Also valid (C-style)
```

**Declare and create (size known, default values assigned):**
```java
int[] numbers = new int[5];
// Creates array of 5 integers, default values = 0
```

**Default values in arrays**

| Data Type    | Default Value |
|--------------|---------------|
| byte         | 0             |
| int          | 0             |
| long         | 0L            |
| float        | 0.0f          |
| double       | 0.0d          |
| char         | '\u0000' (null character) |
| boolean      | false         |
| Reference types (e.g., String, objects) | null |

**Declare and initialize (values known):**
```java
int[] numbers = {10, 20, 30, 40, 50};
String[] cars = {"Volvo", "BMW", "Ford"};
```

**Two-step (declare first, assign later):**
```java
int[] numbers;
numbers = new int[]{10, 20, 30, 40, 50};
```

---

## 3. Access & Assign
```java
int[] nums = new int[3];
nums[0] = 10;
System.out.println(nums[0]); // prints 10
```

---

## 4. `.length` Property
- `.length` gives the size of the array.
- **Note**: `.length` is a **property**, not a method.  
  ~~`.length()`~~ ❌

```java
int [] myNum = {10, 20, 30, 40};
System.out.println(myNum.length); // prints 4
```

---

## 5. Looping Through Arrays

### Basic `for` loop  
Uses index to access elements.
```java
int[] numbers = {10, 20, 30, 40};

for (int i = 0; i < numbers.length; i++) {
    System.out.println("Index " + i + ": " + numbers[i]);
}
```

### Enhanced `for-each` loop  
Shorter, no index, but cannot change array elements directly.
```java
for (int num : numbers) {
    System.out.println(num);
}
```

✅ Use **basic for loop** if you need index or want to update elements.  
✅ Use **enhanced for-each** for simple read-only traversal.  

---

## 6. Common Operations / Examples
- Print all values
- Calculate sum, average, min, max
- Assign random values

---
