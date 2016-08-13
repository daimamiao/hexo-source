---
title: 'LeetCode 121: Best Time to Buy and Sell Stock I, II, III'
date: 2016-08-11 13:56:26
tags: [LeetCode, Dynamic Programming]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Say you have an array for which the ith element is the price of a given stock on day i.If you were only permitted to complete at most one transaction <!--more-->(ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

**Example 1:**
>Input: [7, 1, 5, 3, 6, 4]
Output: 5
max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)

**Example 2:**
>Input: [7, 6, 4, 3, 1]
Output: 0
In this case, no transaction is done, i.e. max profit = 0.

### Code
```c
int maxProfit(int* prices, int pricesSize) {
    int low = prices[0];
    int profit = 0;
    for (int i = 0; i < pricesSize; i++) {
        if (low > prices[i]) {
            low = prices[i];
        } else if (prices[i] - low > profit) {
            profit = prices[i] - low;
        }
    }
    return profit;
}
```
## Best Time to Buy and Sell Stock II
Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).
```c
int maxProfit(int* prices, int pricesSize) {
    int low = prices[0];
    int profit = 0;
    for (int i = 0; i < pricesSize; i++) {
        if (low > prices[i]) {
            low = prices[i];
        } else {
            profit = profit + prices[i] - low;
            low = prices[i];
        }
    }
    return profit;
}
```
## Best Time to Buy and Sell Stock III
Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete at most two transactions.

**Note:**
You may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).
```c
int maxProfit(int* prices, int pricesSize) {
    int maxProfit[pricesSize];
    int maxRevealProfit[pricesSize];
    maxProfit[0] = 0;
    maxRevealProfit[pricesSize - 1] = 0;
    int low = prices[0];
    int profit = 0;
    for (int i = 0; i < pricesSize; i++) {
        if (low > prices[i]) {
            low = prices[i];
        } else if (prices[i] - low > profit) {
            profit = prices[i] - low;
        }
        maxProfit[i] = profit;
    }
    profit = 0;
    int high = prices[pricesSize - 1];
    for (int i = pricesSize - 2; i >= 0; i--) {
        if (high < prices[i]) {
            high = prices[i];
        } else if (profit < high - prices[i]){
            profit = high - prices[i];
        }
        maxRevealProfit[i] = profit;
    }
    int res = 0;
    for(int i = 0; i < pricesSize; i++){
        int tmp = maxProfit[i] + maxRevealProfit[i];
        if(res < tmp) {
            res = tmp;
        }
    }
    return res;
}
```