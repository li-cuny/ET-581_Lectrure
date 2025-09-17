# Nested For Loops in 2D Arrays (Java)

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
int[] firstRow = arr[0]; // first elment of 2d array which is {1, 2, 3},
for (int c = 0; c < firstRow.length; c++) {
    System.out.print(firstRow[c] + " ");
}
```

### Second Row

``` java
int[] secondRow = arr[1]; // second elment of 2d array which is  {4, 5, 6},
for (int c = 0; c < secondRow.length; c++) {
    System.out.print(secondRow[c] + " ");
}
```

### Third Row

``` java
int[] thirdRow = arr[2]; // third elment of 2d array which is   {7, 8, 9}
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

-   `arr.length` → number of rows.\
-   `arr[r].length` → number of columns in row `r`.\
-   Outer loop (`r`) = rows.\
-   Inner loop (`c`) = columns.




nested for loops
example:
int[][] arr  = {
    {1,2,3},
    {4,5,6},
    {7,8.9}
}

we can get each row by
int [] firstRow = arr[0]; // so first element of 2d array is {1,2,3} which is 1d array
print first row (row index is 0) of the 2d array
int[] firstRow = arr[0];
for(int c = 0; c<firstRow.length; c++){
    System.out.print(firstRow[c]);
    // System.out.print( arr[0][c] );
}
print second row (row index is 1) of the 2d array
int[] secondRow = arr[0];
for(int c = 0; c<secondRow.length; c++){
    System.out.print( secondRow[c] );
    // System.out.print( arr[1][c] );
}
print third row (row index is 2) of the 2d array
int[] thirdRow = arr[0];
for(int c = 0; c<thirdRow.length; c++){
    System.out.print(thirdRow[c];)
    //System.out.print( arr[2][c] );
}
since the format of print a single row is repeating.
// print a single row
for(int c=0; c< row.length; c++){
    System.out.print(arr[rowIndex][c]);
}
we want to using another for loop to repeat print row of 2d array

for (int r =0; r<row.length; r++){
    // print a single row
}
so it becomes 
for (int r = 0; r < arr.length; r++){ // repeat 3 times (first row , second row, third row)
    for (int c=0; row.length; c++){ // print a single row
        System.out.print(arr[r][c]);
    }
}
