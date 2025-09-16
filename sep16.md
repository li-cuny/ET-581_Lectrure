# Java Arrays and Related Concepts

## 1. Correct Ways to Create Arrays

| Way | Syntax | Notes |
|-----|-------|------|
| With values | `int[] a = {1, 2, 3};` <br> or `int[] a = new int[]{1, 2, 3};` ✅ | Use when you know values |
| With size only | `int[] a = new int[3];` ✅ | Creates array with default values (`0` for int) |
| Size + values | `int[] a = new int[3]{1,2,3};` ❌ | Not allowed in Java |

---

## 2. Multi-Dimensional Arrays

- Essentially arrays of arrays (e.g., 2D tables).
- Access elements with `[row][col]`.
- Use **nested loops** to traverse.

### Example:
```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};

System.out.println(matrix[0][1]); // prints 2
```

### Nested Loop Example:
```java
int[][] a = {
    {1, 2, 3, 4},
    {4, 5, 6, 7},
    {7, 8, 9, 10}
}; // 3 rows, 4 columns

for(int i = 0; i < a.length; i++){
    for(int j = 0; j < a[i].length; j++){
        System.out.print(a[i][j] + " ");
    }
    System.out.println();
}
```
## 3. create 2D Arrays in different ways

### a. Using Array Literals (Immediate Initialization)

You define the values at the same time you create the array.
```java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
// Jagged array
int[][] jagged = {
    {1, 2, 3},
    {4, 5},
    {6, 7, 8}
};
```
### b. `new` Keyword with Size
```java
int[][] arr = new int[3][4]; // 3 rows, 4 columns
// jagged
int[][] jagged = new int[3][]; // 3 rows, column size not defined yet
// [null, null, null]
jagged[0] = new int[2]; // row 0 has 2 columns
jagged[1] = new int[4]; // row 1 has 4 columns
jagged[2] = new int[1]; // row 2 has 1 column
// [[0, 0], [0, 0, 0, 0], [0]]
```

---

## 3. Shallow Copy vs Deep Copy

### Shallow Copy
- Copies **reference only**.
- Both variables point to the **same array**.
```java
int[] a = {1, 2, 3};
int[] b = a;  // shallow copy
b[0] = 99;

System.out.println(a[0]); // 99
```

### Deep Copy
- Creates a **new array** and copies all values.
- Arrays are **independent**.
```java
int[] a = {1, 2, 3};
int[] b = new int[a.length];

for (int i = 0; i < a.length; i++) {
    b[i] = a[i];
}

b[0] = 99;

System.out.println(a[0]); // 1
System.out.println(b[0]); // 99
```

---

## 4. Arrays Utility Class (`java.util.Arrays`)

| Method | Description | Example |
|--------|-------------|---------|
| `Arrays.fill(array, value)` | Fill array with value | `Arrays.fill(arr, 1);` |
| `Arrays.sort(array)` | Sort array ascending | `Arrays.sort(arr);` |
| `Arrays.copyOf(array, newLength)` | Copy array with new size | `int[] newArr = Arrays.copyOf(arr, 10);` |
| `Arrays.equals(arr1, arr2)` | Compare 1D arrays | `Arrays.equals(arr1, arr2);` |
| `Arrays.toString(array)` | Convert 1D array to string | `System.out.println(Arrays.toString(arr));` |
| `Arrays.deepEquals(arr1, arr2)` | Compare multidimensional arrays | `Arrays.deepEquals(matrix1, matrix2);` |
| `Arrays.deepToString(array)` | Convert multidimensional array to string | `System.out.println(Arrays.deepToString(matrix));` |

---

## 5. Sorting Arrays (Bubble Sort Example)

```java
int[] arr = {5, 3, 8, 4, 2};
int n = arr.length;

for (int i = 0; i < n - 1; i++) {
    for (int j = 0; j < n - i - 1; j++) {
        if (arr[j] > arr[j + 1]) {
            int temp = arr[j];
            arr[j] = arr[j + 1];
            arr[j + 1] = temp;
        }
    }
}

System.out.println(Arrays.toString(arr)); // [2, 3, 4, 5, 8]
```

- **Idea:** Largest unsorted element “bubbles up” after each pass.

---

## 6. Generating Random Numbers

### Using `Math.random()`
```java
double r = Math.random();
int n = (int)(Math.random() * 10); // 0 to 9
```

### Using `Random` Class
```java
import java.util.Random;

Random rand = new Random();

// Random double 0.0 <= x < 1.0
double rDouble = rand.nextDouble();

// Random int between 0 and 9
int rInt = rand.nextInt(10);

// Random boolean
boolean rBool = rand.nextBoolean();
```
- More versatile than `Math.random()`.
- Can set a **seed** for reproducible results.

---
