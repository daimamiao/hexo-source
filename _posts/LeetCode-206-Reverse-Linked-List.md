---
title: 'LeetCode 206: Reverse Linked List'
date: 2016-08-02 08:30:43
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Reverse a singly linked list.**Hint:** A linked list can be reversed either iteratively or recursively. Could you implement both?<!--more-->
### 题意
翻转该单链表
### 思路
使用迭代法或者递归法皆可实现。
### 代码
C语言版本：
iteratively(迭代方法)
``` c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* reverseList(struct ListNode* head) {
    if (NULL == head){
        return head;
    }
    struct ListNode *p = head;
    p = head->next;
    head->next = NULL;
    while (p != NULL){
        struct ListNode *pNext = p->next;
        p->next = head;
        head = p;
        p = pNext;
    }
    return head;
}
```