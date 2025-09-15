# Java Random Number

## Math.random()
- **Type:** Static method
- **Returns:** double (0.0 ≤ x < 1.0)
- **Simple, no object needed**

### Examples
```java
// Random double between 0.0 and 1.0
double r = Math.random();

// Random int between 0 and 9
int n = (int)(Math.random() * 10);

```
### Random class (java.util.Random)

Type: Class, need to create instance

Can generate: int, double, boolean, float, long

### Examples
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


## 7. Multi-Dimensional Arrays
- Array of arrays (e.g., 2D tables)
- Access with `[row][col]`
- Use nested loops

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};

System.out.println(matrix[0][1]); // prints 2
```
```java
int[][] a = {
                {1,2,3,4},
                {4,5,6,7},
                {7,8,9,10}
            }; // a[3][3]
    for(int i=0; i < a.length; i++){
      for(int j=0; j<a[i].length; j++){
        System.out.print(a[i][j] + " ");
      }
      System.out.println();
    }
```

---

## 8. `Arrays` Utility Class
Java provides a built-in utility class `java.util.Arrays` that makes working with arrays easier.  
It is **static**, so you don’t need to create an object — just call its methods directly.

| Method                            | Description                         | Example                                     |
|-----------------------------------|-------------------------------------|---------------------------------------------|
| `Arrays.fill(array, value)`       | Fill array with a value             | `Arrays.fill(arr, 1);`                      |
| `Arrays.toString(array)`          | Convert array to a string           | `System.out.println(Arrays.toString(arr));` |
| `Arrays.sort(array)`              | Sort array in ascending order       | `Arrays.sort(arr);`                         |
| `Arrays.copyOf(array, newLength)` | Copy array to new size              | `int[] newArr = Arrays.copyOf(arr, 10);`    |
| `Arrays.equals(arr1, arr2)`       | Compare two arrays                  | `Arrays.equals(arr, arr2);`                 |

---
