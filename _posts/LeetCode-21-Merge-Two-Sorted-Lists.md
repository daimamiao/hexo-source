---
title: 'LeetCode 21: Merge Two Sorted Lists'
date: 2016-08-02 10:45:27
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.<!--more-->
### 题意
融合两个已经排好序的链表，并返回一个新表。
### 思路
先找到表头，然后做个循环不断排序下去即可。
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
struct ListNode* mergeTwoLists(struct ListNode* l1, struct ListNode* l2) {
    if (l1 == NULL){
        return l2;
    } 
    if (l2 == NULL){
        return l1;
    } 
    
    struct ListNode* head = NULL;
    
    // find the first element 
    if (l1->val < l2->val){
        head = l1;
        l1 = l1->next;
    }else{
        head = l2;
        l2 = l2->next;
    }
    
    struct ListNode* p = head;
    while(l1&&l2){
        if (l1->val < l2->val){
            p->next = l1;
            l1 = l1->next;
        }else{
            p->next = l2;
            l2 = l2->next;
        }
        p = p->next;
    }
    if(l1){
        p->next=l1;
    }else{
        p->next=l2;
    }    
    return head;
}
```
**结果：**
`208 / 208 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`