---
title: 'LeetCode 9: Palindrome Number'
date: 2016-08-08 15:52:04
tags: [LeetCode, Math]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Determine whether an integer is a palindrome. Do this without extra space. <!--more-->
### 代码
```c
bool isPalindrome(int x) {
    if (x < 0 || (x!=0 && x%10==0)) {
        return false;
    }
    int sum = 0;
    while (x > sum) {
        sum = sum*10 + x%10;
        x /= 10;
    }
    return (x==sum)||(x==sum/10);
    
}
```