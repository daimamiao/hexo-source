---
title: 'LeetCode 74:Search a 2D Matrix'
date: 2016-08-13 11:09:30
tags: [LeetCode, Array, Binary Search]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties: <!--more-->

Integers in each row are sorted from left to right.
The first integer of each row is greater than the last integer of the previous row.
For example,

Consider the following matrix:

>[
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]

Given target = `3`, return `true`.

### Code
```c
bool searchMatrix(int** matrix, int matrixRowSize, int matrixColSize, int target) {
    int low = 0;
    int high = matrixRowSize*matrixColSize - 1;
    int mid = 0;
    while (low < high) {
        mid = (low + high) / 2;
        if (matrix[mid / matrixColSize][mid % matrixColSize] > target) {
            high = mid - 1;
        } else if (matrix[mid / matrixColSize][mid % matrixColSize] < target) {
            low = mid + 1;
        } else {
            return 1;
        }
    }
    if (matrix[low / matrixColSize][low % matrixColSize] != target) {
        return 0;
    }
    return 1;
}
```