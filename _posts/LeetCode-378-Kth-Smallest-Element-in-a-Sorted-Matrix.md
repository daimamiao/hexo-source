---
title: 'LeetCode 378:Kth Smallest Element in a Sorted Matrix'
date: 2016-08-13 10:37:11
tags: [LeetCode, Array, Binary Search]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a n x n matrix where each of the rows and columns are sorted in ascending order, find the kth smallest element in the matrix.

Note that it is the kth smallest element in the sorted order, not the kth distinct element.

**Example:**

>matrix = [
   [ 1,  5,  9],
   [10, 11, 13],
   [12, 13, 15]
],
k = 8,

return 13.
**Note:**
You may assume k is always valid, `1 ≤ k ≤ n2`.

### Code
```c
int kthSmallest(int** matrix, int matrixRowSize, int matrixColSize, int k) {
    int minVal = matrix[0][0];
    int maxVal = matrix[matrixRowSize-1][matrixColSize-1];
    int midVal = 0;
    int count = 0;
    while (minVal < maxVal) {
        midVal = (minVal + maxVal) / 2;
        for (int i  = 0; i < matrixRowSize && matrix[i][0] <= midVal; i++) {
            for (int j = 0; j < matrixColSize; j++) {
                if (matrix[i][j] <= midVal) {
                    count++;   
                }
            }
        }
        if (k <= count) {
            maxVal = midVal;
        } else {
            minVal = midVal + 1;
        }
        count = 0;
    }
    return minVal;
}
```