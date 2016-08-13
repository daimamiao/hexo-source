---
title: 'LeetCode 319: Bulb Switcher'
date: 2016-08-08 16:15:41
tags: [LeetCode, Math]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
There are n bulbs that are initially off. You first turn on all the bulbs. Then, you turn off every second bulb. <!--more-->  On the third round, you toggle every third bulb (turning on if it's off or turning off if it's on). For the ith round, you toggle every i bulb. For the nth round, you only toggle the last bulb. Find how many bulbs are on after n rounds.

Example:
> Given n = 3. 
At first, the three bulbs are [off, off, off].
After first round, the three bulbs are [on, on, on].
After second round, the three bulbs are [on, off, on].
After third round, the three bulbs are [on, off, off]. 
So you should return 1, because there is only one bulb is on.

### 思路
用数学的方法来思考这道题，会发现很简单。首先，决定一盏灯最后的亮灭取决于她所处在的序号。比如，6号灯最后一定是灭的，为什么呢？因为在n次操作中，只有她的因数次才能切换她的亮灭，比如第1次、第2次、第3次、第6次操作，又第1次是开，那么低6次后，她就灭了。所以要想亮，那么这个数要为有奇数个因数的数才行，而我们知道只有能开平方的数，有奇数个因数，因为她有一个不是成对出现的因数。所以要知道最后有几个灯是亮的，只要找到有几个小于n的能开平方数的数即可。而要计算一个数之下有多少小于或等于它的平方数，使用一个开平方用的函数就可以了。
### 代码
```c
int bulbSwitch(int n) {
    return sqrt(n);
}
```