---
title: 'LeetCode 160: Intersection of Two Linked Lists'
date: 2016-08-03 11:26:12
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Write a program to find the node at which the intersection of two singly linked lists begins.For example, the following two linked lists:<!--more-->
```
A:         a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3
begin to intersect at node c1.
```
**Notes:**
* If the two linked lists have no intersection at all, return null.
* The linked lists must retain their original structure after the function returns.
* You may assume there are no cycles anywhere in the entire linked structure.
* Your code should preferably run in O(n) time and use only O(1) memory.

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
struct ListNode *getIntersectionNode(struct ListNode *headA, struct ListNode *headB) {
  struct ListNode *LA, *LB;    
    struct ListNode *h1, *h2;
    int lenA=0, lenB=0, step=0;

    if(!headA || !headB)
        return NULL;
    LA = headA;
    LB = headB;
    while(LA){
        lenA++;
        LA = LA->next;
    }
    while(LB){
        lenB++;
        LB = LB->next;
    }
    if(lenA >= lenB{
        step = lenA - lenB;
        h1 = headA;
        h2 = headB;
    }else{
        step = lenB - lenA;
        h1 = headB;
        h2 = headA;
    }
    while(h1 && step){
        step--;
        h1 = h1->next;
    }
    while(h1 && h2){
        if(h1->val == h2->val)
            return h1;
        h1 = h1->next;
        h2 = h2->next;
    }
    return NULL;
}
```
`42 / 42 test cases passed.`
Status: `Accepted`
Runtime: `32 ms`