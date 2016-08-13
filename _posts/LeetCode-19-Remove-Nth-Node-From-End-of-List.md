---
title: 'LeetCode 19: Remove Nth Node From End of List'
date: 2016-08-03 18:35:26
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a linked list, remove the nth node from the end of list and return its head. For example,Given linked list: 1->2->3->4->5, and n = 2.<!--more-->After removing the second node from the end, the linked list becomes `1->2->3->5.`
**Note:**
Given n will always be valid.
Try to do this in one pass.
### 思路
两个指针，当一个指向末尾时，另一个恰好指向要删除节点的前一个节点处。
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
struct ListNode* removeNthFromEnd(struct ListNode* head, int n) {
    struct ListNode* front = head;
    struct ListNode* behind = head;
    
    while ( front ){
        front = front -> next;
        if ( n-- < 0 ){
            behind = behind->next;
        }
    }
    
    if (n == 0) {
        head = head->next;
    }else {
        behind->next = behind->next->next;
    }
    return head;
}
```