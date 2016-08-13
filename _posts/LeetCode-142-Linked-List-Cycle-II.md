---
title: 'LeetCode 142: Linked List Cycle II'
date: 2016-08-04 12:49:05
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a linked list, return the node where the cycle begins. If there is no cycle, return null. **Note:** Do not modify the linked list. Follow up: Can you solve it without using extra space? <!--more-->
### 思路
还是使用快慢指针的做法，先判断是否有环，没环的话直接返回`null`，否则在有环的情况下，在slow指针和fast指针第一次相遇处，让fast指针停下，slow继续前进，与此同时，一个从head开始的rHead指针也一起前进。最后rHead与slow指针相遇处就是环的开始之处。
### 代码
C语言版本：
```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode *detectCycle(struct ListNode *head) {
    struct ListNode* fast = head;
    struct ListNode* slow = head;
    struct ListNode* rHead = head;
    
    while (fast && fast -> next) {
        fast = fast -> next -> next;
        slow = slow -> next;
        if (slow == fast){
            break;
        }
    }
    if ( !fast || !fast -> next){
        return false;
    }
    while ( slow != rHead){
        rHead = rHead -> next;
        slow = slow -> next;
    }
    return rHead;
}
```
`16 / 16 test cases passed.`
Status: `Accepted`
Runtime: `8 ms`