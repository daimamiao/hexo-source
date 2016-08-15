---
title: 'LeetCode 33:Search a 2D Matrix II'
date: 2016-08-14 10:28:31
tags: [LeetCode, Binary Search]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
一开始看到这题，脑子一下子转不过来，就想着从左上角开始比较，但是如果发现目标值比较大的话，那么可以向下遍历比较也可以向右比较，这时候我就反应不过来了。后来看了别人的解法，才发现如果一开始就从右上角开始比较，那么上面的问题就没有了。 <!--more-->

Write an efficient algorithm that searches for a value in an m x n matrix. This matrix has the following properties:

- Integers in each row are sorted in ascending from left to right.
- Integers in each column are sorted in ascending from top to bottom.
For example,

Consider the following matrix:

>[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]

Given target = `5`, return `true`.

Given target = `20`, return `false`.
### Code
```c
bool searchMatrix(int** matrix, int matrixRowSize, int matrixColSize, int target) {
    int row = 0;
    int col = matrixColSize - 1;
    while(row < matrixRowSize && col >= 0) {
        if (matrix[row][col] == target) {
            return 1;
        } else if (matrix[row][col] > target) {
            col--;
        } else {
            row++;
        }
    }
    return 0;
}
```