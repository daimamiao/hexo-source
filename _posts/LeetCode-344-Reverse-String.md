---
title: 'LeetCode 344: Reverse String'
date: 2016-08-05 17:12:25
tags: [LeetCode, String]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Write a function that takes a string as input and returns the string reversed. Example: Given `s = "hello"`, return `"olleh"`. <!--more-->
### 代码
C语言版本：
```c
char* reverseString(char* s) {
    int left = 0;
    int right = strlen(s) - 1;
    
    while (left<right){
        s[left] ^= s[right];
        s[right] ^= s[left];
        s[left] ^= s[right];
        left++;
        right--;
    }
    return s;
}
```
`476 / 476 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`
C++版本：
```java
class Solution {
public:
    string reverseString(string s) {
        int l = 0, r = s.size() - 1;
        while (l < r){
            swap(s[l++], s[r--]);
        }
        return s;
    }
};
```
`476 / 476 test cases passed.`
Status: `Accepted`
Runtime: `12 ms`