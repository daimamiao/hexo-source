---
title: 'LeetCode 118:pascals Triangle'
date: 2016-08-16 10:07:02
tags:
categories:
thumbnail:
---
Given numRows, generate the first numRows of Pascal's triangle.

For example, given numRows = 5,
Return
```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

### Code
```c
/**
 * Return an array of arrays.
 * The sizes of the arrays are returned as *columnSizes array.
 * Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
 */
int** generate(int numRows, int** columnSizes) {
    if (numRows <= 0) {
        columnSizes = NULL;
        return NULL;
    }
    int *columns = (int*)malloc(sizeof(int)*numRows);
    columns[0] = 1;
    int** pascal = (int**)malloc(sizeof(int*)*numRows);
    pascal[0] = (int*)malloc(sizeof(int));
    pascal[0][0] = 1;
    
    for (int i = 1; i < numRows; ++i) {
        columns[i] = i + 1;
        pascal[i] = (int*)malloc(sizeof(int) * columns[i]);

        pascal[i][0] = 1;
        for (int j = 1; j < i; ++j) {
            pascal[i][j] = pascal[i-1][j-1] + pascal[i-1][j];
        }
        pascal[i][i] = 1;
    }
    
    *columnSizes = columns;
    return pascal;
}
```