---
title: 'LeetCode 11: Container With Most Water'
date: 2016-08-12 07:59:36
categories: LeetCode
tags: [LeetCode, Array]
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given n non-negative integers a1, a2, ..., an, where each represents a point at coordinate (i, ai). <!--more-->n vertical lines are drawn such that the two endpoints of line i is at (i, ai) and (i, 0). Find two lines, which together with x-axis forms a container, such that the container contains the most water.
**Note:** You may not slant the container.
### 思路
>有两个指针i和j分别指向头和尾， 如果a[i] < a[j], 则i++,否则j--:
证明：
对任意ｋ< j：
都有(k-i)*min(a[k],a[i]) < (j-i)min(a[j],a[i]) = (j-i)a[i]
**因为:**
(k-i) < (j-i)
min(a[k],a[i]) < a[i] < min(a[j],a[i])
所以此种情况移动j只能得到更小的值， 移动j无用， 只能移动i。 反之亦然。

### Code
```c
int maxArea(int* height, int heightSize) {
    int left = 0;
    int right = heightSize - 1;
    int i = 0;
    int max = 0;
    int temp = 0;
    while (left < right) {
        if (height[left] <= height[right]) {
            temp = (right - left) * height[left];
            left++;
            if (temp >= max) {
                max = temp;
            }
            i++;
        } else {
            temp = (right - left) * height[right];
            right--;
            if (temp >= max) {
                max = temp;
            }
            i++;
        }
    }
    return max;
}
```
