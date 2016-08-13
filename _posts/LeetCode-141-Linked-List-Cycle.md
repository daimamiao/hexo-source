---
title: 'LeetCode 141: Linked List Cycle'
date: 2016-08-03 21:15:18
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a linked list, determine if it has a cycle in it. Follow up: Can you solve it without using extra space?<!--more-->
### 思路
设两个指针即快慢指针，只要是一个环，那么跑得快的总能追上跑得慢的。
### 代码
C语言版本：
``` c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
bool hasCycle(struct ListNode *head) {

    struct ListNode* fast = head;
    struct ListNode* slow = head;
    
    while ( fast && fast -> next ){
        fast = fast -> next -> next;
        slow = slow -> next;
        
        if (fast == slow){
            return true;
        }
    }
    return false;
}
```
