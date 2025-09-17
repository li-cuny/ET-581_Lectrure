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
replace cmment with print single row code will become
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
    for (int c = 0; c < arr[r].length; c++) {   // loop over columns in that row
        System.out.print(arr[r][c] + " ");
    }
    System.out.println(); // new line after each row
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




