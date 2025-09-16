# Java Arrays and Related Concepts

## 7. Multi-Dimensional Arrays
- Array of arrays (e.g., 2D tables)
- Access with [row][col]
- Use nested loops

### Example 1:
```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};

System.out.println(matrix[0][1]); // prints 2
```

### Example 2:
```java
int[][] a = {
    {1, 2, 3, 4},
    {4, 5, 6, 7},
    {7, 8, 9, 10}
}; // a[3][4]

for(int i = 0; i < a.length; i++){
    for(int j = 0; j < a[i].length; j++){
        System.out.print(a[i][j] + " ");
    }
    System.out.println();
}
```

---

# Shallow Copy vs Deep Copy in Java

## 🔹 1. Shallow Copy
A **shallow copy** copies only the **reference** of the array. Both variables point to the **same array**.

### Example:
```java
int[] a = {1, 2, 3};
int[] b = a;  // shallow copy
b[0] = 99;

System.out.println(a[0]); // 99 (changed in both)
```
- `a` and `b` refer to the **same array**.  

---

## 🔹 2. Deep Copy
A **deep copy** creates a **new array** and copies the values. Each variable has an **independent copy**.

### Example:
```java
int[] a = {1, 2, 3};
int[] b = new int[a.length];

for (int i = 0; i < a.length; i++) {
    b[i] = a[i];   // copy each element
}

b[0] = 99;

System.out.println(a[0]); // 1 (unchanged)
System.out.println(b[0]); // 99
```
- `a` and `b` are **separate arrays**.

---

## 8. Arrays Utility Class
Java provides `java.util.Arrays` with static methods to simplify array operations.

| Method | Description | Example |
|--------|-------------|---------|
| `Arrays.fill(array, value)` | Fill array with a value | `Arrays.fill(arr, 1);` |
| `Arrays.sort(array)` | Sort array ascending | `Arrays.sort(arr);` |
| `Arrays.copyOf(array, newLength)` | Copy array to new size | `int[] newArr = Arrays.copyOf(arr, 10);` |
| `Arrays.equals(arr1, arr2)` | Compare 1D arrays | `Arrays.equals(arr1, arr2);` |
| `Arrays.toString(array)` | Convert 1D array to string | `System.out.println(Arrays.toString(arr));` |
| `Arrays.deepEquals(arr1, arr2)` | Compare multidimensional arrays | `Arrays.deepEquals(matrix1, matrix2);` |
| `Arrays.deepToString(array)` | Convert multidimensional array to string | `System.out.println(Arrays.deepToString(matrix));` |

---

## More Examples of For Loops

### Implement Array Methods
- Fill array  
- Copy array to larger size  

### Sorting
- Sort array (Bubble Sort)
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

System.out.println(Arrays.toString(arr));
```
- **Idea:** After each pass, the largest unsorted element “bubbles up” to its correct position.

### Print Patterns
- Print triangles using loops

---

## Java Random Numbers

### Math.random()
- **Type:** Static method  
- **Returns:** double (0.0 ≤ x < 1.0)  
- Simple, no object needed

#### Examples:
```java
// Random double between 0.0 and 1.0
double r = Math.random();

// Random int between 0 and 9
int n = (int)(Math.random() * 10);
```

### Random Class (java.util.Random)
- **Type:** Class, requires instance  
- Can generate: int, double, boolean, float, long

#### Examples:
```java
import java.util.Random;
Random rand = new Random(); // or new Random(seed)

// Random double 0.0 <= x < 1.0
double rDouble = rand.nextDouble();

// Random int between 0 and 9
int rInt = rand.nextInt(10);

// Random boolean
boolean rBool = rand.nextBoolean();
```
