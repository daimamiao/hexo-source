---
title: 'LeetCode 48: Rotate Image'
date: 2016-08-12 11:13:48
categories: LeetCode
tags: [LeetCode, Array]
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
You are given an n x n 2D matrix representing an image. Rotate the image by 90 degrees (clockwise). <!--more-->

Follow up:
Could you do this in-place?

### Code
```c
/*
 * clockwise rotate
 * first reverse up to down, then swap the symmetry 
 * 1 2 3     7 8 9     7 4 1
 * 4 5 6  => 4 5 6  => 8 5 2
 * 7 8 9     1 2 3     9 6 3
*/
void rotate(int** matrix, int matrixRowSize, int matrixColSize) {
    for (int i = 0; i < matrixRowSize / 2; i++) {
		for (int j = 0; j < matrixColSize; j++) {
			matrix[i][j] ^= matrix[matrixRowSize - 1 - i][j];
			matrix[matrixRowSize - 1 - i][j] ^= matrix[i][j];
			matrix[i][j] ^= matrix[matrixRowSize - 1 - i][j];
		}
	}
	for (int i = 0; i < matrixRowSize - 1; i++) {
		for (int j = i + 1; j < matrixColSize; j++) {
			matrix[i][j] ^= matrix[j][i];
			matrix[j][i] ^= matrix[i][j];
			matrix[i][j] ^= matrix[j][i];
		}
	}
}
```