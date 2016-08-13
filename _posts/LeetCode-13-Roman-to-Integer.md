---
title: 'LeetCode 13: Roman to Integer'
date: 2016-08-05 17:34:44
tags: [LeetCode, String]
categories: LeetCode
series: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a roman numeral, convert it to an integer.3999 / 3999 test cases passed. <!--more-->
### 代码
C语言版本：
```c
int romanCharToInt(char c){
    switch (c) {
        case 'I': 	return 1;
		case 'V':	return 5;
		case 'X':	return 10;
		case 'L':	return 50;
		case 'C':	return 100;
		case 'D':	return 500;
		case 'M':	return 1000;
		default:	return 0;
    }
}
int romanToInt(char* s) {
    int res = 0;
    int size = strlen(s);
    for (int i = 0; i < size; i++) {
        if (romanCharToInt(s[i]) < romanCharToInt(s[i + 1])){
            res -= romanCharToInt(s[i]);
        } else {
            res += romanCharToInt(s[i]);
        }
    }
    return res;
}
```
`3999 / 3999 test cases passed.`
Status: `Accepted`
Runtime: `24 ms`
C++版本：
```java
class Solution {
public:
    int romanToInt(string s) {
            int num = 0;
            int size = s.size();
            for (int i = 0; i < size; i++) {
            	if (i < (size - 1) && romanCharToInt(s[i]) < romanCharToInt(s[i + 1])) {
            		num -= romanCharToInt(s[i]);
            	} else {
    				num += romanCharToInt(s[i]);
    			}
            }
            return num;
        }
        int romanCharToInt(char c) {
        	switch (c) {
        		case 'I': 	return 1;
        		case 'V':	return 5;
        		case 'X':	return 10;
        		case 'L':	return 50;
        		case 'C':	return 100;
        		case 'D':	return 500;
        		case 'M':	return 1000;
        		default:	return 0;
        	}
        }
};
```
`3999 / 3999 test cases passed.`
Status: `Accepted`
Runtime: `36 ms`
java版本：
```java
public class Solution {
    public int romanToInt(String s) {
        //：Ⅰ（1）Ⅴ（5）Ⅹ（10）L（50）C（100）D（500）M（1000） 
        // rules:位于大数的后面时就作为加数；位于大数的前面就作为减数
        //eg：Ⅲ=3,Ⅳ=4,Ⅵ=6,ⅩⅨ=19,ⅩⅩ=20,ⅩLⅤ=45,MCMⅩⅩC=1980
        //"DCXXI"
        if(s == null || s.length() == 0) return 0;
        int len = s.length();
        HashMap<Character,Integer> map = new HashMap<Character,Integer>();
        map.put('I',1);
        map.put('V',5);
        map.put('X',10);
        map.put('L',50);
        map.put('C',100);
        map.put('D',500);
        map.put('M',1000);
        int result = map.get(s.charAt(len -1));
        int pivot = result;
        for(int i = len -2; i>= 0;i--){
            int cur = map.get(s.charAt(i));
            if(cur >=  pivot){
                result += cur;
            }else{
                result -= cur;
            }
            pivot = cur;
        }
        return result;
    }
}
```
`3999 / 3999 test cases passed.`
Status: `Accepted`
Runtime: `24 ms`