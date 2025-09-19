# Nested For Loops in 2D Arrays 

## Example Array

``` java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

------------------------------------------------------------------------

## Printing Rows Manually

### First Row

``` java
int[] firstRow = arr[0]; // first elment of 2d array which is 1d array {1, 2, 3},
for (int c = 0; c < firstRow.length; c++) {
    System.out.print(firstRow[c] + " ");
}
```

### Second Row

``` java
int[] secondRow = arr[1]; // second elment of 2d array which is 1d array {4, 5, 6},
for (int c = 0; c < secondRow.length; c++) {
    System.out.print(secondRow[c] + " ");
}
```

### Third Row

``` java
int[] thirdRow = arr[2]; // third elment of 2d array which is 1d array {7, 8, 9}
for (int c = 0; c < thirdRow.length; c++) {
    System.out.print(thirdRow[c] + " ");
}
```
## repeating print a single row
since the logic is repeating on print row, 
adding another loop for changing row number (row 0 -> row 2)
```java
for(int r=0;r<arr.length; r++){// row 0 -> row2
    // print a single row
}
```
adding print single row logic at `//print a single row` comment
```java
for(int r=0;r<arr.length; r++){// row 0 -> row2
    // print a single row
    int[] eachRow = arr[r];
    for (int c = 0; c < eachRow.length; c++) {
        System.out.print(eachRow[c] + " ");
    }
}
```
so we finished nested for loop to print 2d array.
in above code `eachRow = arr[r]` so we can replace eachRow with arr[r]
so it becomes


``` java
for (int r = 0; r < arr.length; r++) {          // loop over rows
    // print a single row
    for (int c = 0; c < arr[r].length; c++) {   // loop over columns 
        System.out.print(arr[r][c] + " ");
    }
    System.out.println(); // add new line after each row
}
```

------------------------------------------------------------------------

## Output

    1 2 3 
    4 5 6 
    7 8 9 

------------------------------------------------------------------------

## Key Points

-   `arr.length` → number of rows.
-   `arr[r].length` → number of columns in row `r`.
-   Outer loop (`r`) = rows
-   Inner loop (`c`) = columns.

# Bubble Sort  

## Example Array
```java
int[] arr = {5, 2, 9, 1, 3};
```

---

## Sort Manually  

### Step 1: Sort first number  
Goal: bubble the largest number (`9`) to the end → `[*, *, *, *, 9]`  

```java
for (int j = 0; j < arr.length - 1; j++) { 
    int a = arr[j];      // current number
    int b = arr[j + 1];  // next number
    if (a > b) {
        // swap arr[j] and arr[j+1]
    }
}
```
[[one number sort steps ](https://li-cuny.github.io/ET-581_Lectrure/html/bubble_demo_1.html)]

⚠️ Note: the condition is `j < arr.length - 1`, not `i < arr.length - 1`,  
because `b = arr[j+1]` could go out of bounds.  

After this loop, the biggest value (`9`) is at the end.  

---

### Step 2: Sort second number  
Goal: bubble the second-biggest (`5`) to the second-to-last spot → `[*, *, *, 5, 9]`  

```java
for (int j = 0; j < arr.length - 1; j++) { 
    int a = arr[j];
    int b = arr[j + 1];
    if (a > b) {
        // swap arr[j] and arr[j+1]
    }
}
```

---

### Step 3: Sort the rest  
- Bubble `3` → `[*, *, 3, 5, 9]`  
- Bubble `2` → `[*, 2, 3, 5, 9]`  
- Bubble `1` → `[1, 2, 3, 5, 9]`  

---

## Using Nested Loops  

Instead of repeating the same loop for each number,  
we use another `for` loop to handle repeated sort on number.  

```java
for (int i = 0; i < arr.length; i++) { // repeat n times
    // sort one number to the location
    for (int j = 0; j < arr.length - 1; j++) { 
        int a = arr[j];
        int b = arr[j + 1];
        if (a > b) {
            // swap arr[j] and arr[j+1]
        }
    }
}
```
swapping numbers in `arr[j]` and `arr[j+1]`
```java
int temp = arr[j];
arr[j] = arr[j + 1];
arr[j + 1] = temp;
```
---

## Final Output
After all passes:  
```
[1, 2, 3, 5, 9]
```

---

✅ This is the **simple version of bubble sort**.  
It can be optimized further by reducing inner loop length each pass (`arr.length - i - 1`) and stopping early if no swaps happen.

| Step        | Array before the Bubble | Already Sorted Elements |
|------------|------------------|------------------------|
| Bubble 9   | [*, *, *, *, *]   | 0 numbers []           |
| Bubble 5   | [*, *, *, *, 9]   | 1 number [9]           |
| Bubble 3   | [*, *, *, 5, 9]   | 2 numbers [5, 9]       |
| Bubble 2   | [*, *, 3, 5, 9]   | 3 numbers [3, 5, 9]    |
| Bubble 1   | [*, 2, 3, 5, 9]   | 4 numbers [2, 3, 5, 9] |
| Bubble one number   | [*, *, ..., s,...,s]    | i numbers [s,...,s] |

Thus, for the inner loop we use `arr.length - i` for sorting each number.  
⚠️ Remember to subtract `1` (`arr.length - i - 1`) because `b = arr[j+1]` otherwise it will go out of the array boundary.

# more loops
## print patterns
using nested for loop to print pattern
```java
Top-Left Triangle:
* * * * * 
* * * * 
* * * 
* * 
* 
```
## print array in column
given array
```java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```
output/print
```
1 4 7
2 5 8
3 6 9
```
---

## Math Class in Java
- `Math.max(x,y)` → maximum of x and y  
- `Math.min(x,y)` → minimum of x and y  
- `Math.sqrt(x)` → square root of x  
- `Math.pow(x,y)` → x raised to power y  
- `Math.abs(x)` → absolute value of x  
- `Math.random()` → random number [0.0, 1.0)  
- `(int)(Math.random() * 101)` → random number [0,100]  

---

## Methods / Functions
- A block of code executed when called.
- Benefits: code reuse.
- Must be defined inside a class.

### Syntax
```java
public class Main {
    static void myMethod() {
        // code
    }
}
```

### Parameters & Arguments
- Parameters → variables inside methods.  
- Arguments → values passed when calling.  

Example:
```java
static void greet(String name) {
    System.out.println("Hello " + name);
}
```

### Return Values
- Use a return type instead of `void`.  
```java
static int add(int a, int b) {
    return a + b;
}
```

### Method Overloading
- Same method name, different parameter list.
```java
int square(int x);
double square(double x);
```