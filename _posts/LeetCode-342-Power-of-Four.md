---
title: 'LeetCode 342: Power of Four'
date: 2016-08-10 10:56:19
tags: [LeetCode, Bit Manipulation]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given an integer (signed 32 bits), write a function to check whether it is a power of 4. <!--more-->
**Example:**
Given num = 16, return true. Given num = 5, return false.
Follow up: Could you solve it without loops/recursion?

### 思路
首先我们可以列出4, 16, 64, 256这几个数的二进制来看一下规律，发现它们都是在偶数位为1，而且只有一位是1，其余位都是0。有了上面这个规律我们就可以结题了。首先，筛选只有一位是1，其余位是0的数，使用`num & (num-1)`即可。再使用`0x55555555`与num作位与操作`&`即可发现，不是我们所要的数经过这步后都是0。到此我们就可以判断出结果了。
### 代码
```c
bool isPowerOfFour(int num) {
    return num > 0 && (num&(num-1)) == 0 && (num & 0x55555555) != 0;
}
```
`1060 / 1060 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`