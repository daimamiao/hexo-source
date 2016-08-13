---
title: 'LeetCode 20: Valid Parentheses'
date: 2016-08-07 10:58:47
tags: [LeetCode, String]
categories: [LeetCode, 算法]
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a string containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.
<!--more-->The brackets must close in the correct order, `"()"` and `"()[]{}"` are all valid but `"(]"` and `"([)]"` are not. 
### 思路
看到这种括弧匹配问题，我首先想到的就是用stack来实现。
### 代码
```c
class Solution {
public:
    bool isValid(string s) {
        stack<char> paren;
        for (char& c : s) {
            switch (c) {
                case '(': 
                case '{': 
                case '[': paren.push(c); break;
                case ')': if (paren.empty() || paren.top()!='(') return false; else paren.pop(); break;
                case '}': if (paren.empty() || paren.top()!='{') return false; else paren.pop(); break;
                case ']': if (paren.empty() || paren.top()!='[') return false; else paren.pop(); break;
                default: ; // pass
            }
        }
        return paren.empty() ;
    }
};
```
C语言版本：
```c
bool isValid(char* s) {
    int len = strlen(s);
    if( len%2 != 0 )
    {
        return false;
    }
    int limit = len/2;
    char *stack = malloc(limit+1);
    int topOfStack = -1;
    for (int i = 0; i < len; i++) {
        if(s[i] == '(' || s[i] == '[' || s[i] =='{') {
            if(topOfStack == limit)
            {
                return false;
            }
            else
            {
                stack[++topOfStack] = s[i];
            }
        }else {
            if(topOfStack == -1)
            {
                return false;
            }
            if( (stack[topOfStack] == '(' && s[i] == ')') || (stack[topOfStack] == '[' && s[i] == ']') || (stack[topOfStack] == '{' && s[i] == '}') ) {
                topOfStack--;
            }
        }
    }
    return topOfStack == -1;
}
```