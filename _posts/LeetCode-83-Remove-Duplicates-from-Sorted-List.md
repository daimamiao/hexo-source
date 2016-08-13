---
title: 'LeetCode 83: Remove Duplicates from Sorted List'
date: 2016-08-03 21:46:45
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a sorted linked list, delete all duplicates such that each element appear only once. For example, Given 1->1->2, return 1->2.Given 1->1->2->3->3, return 1->2->3. <!--more-->
### 思路
由于链表已经排好序，所以直接循环查找重复的节点，没什么好说的，比较简单。
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
struct ListNode* deleteDuplicates(struct ListNode* head) {
    struct ListNode* p = head;
    if ( head ){
        while ( p -> next ){
            if (p -> val != p -> next -> val ){
                p = p -> next;
            }else{
                struct ListNode* tmp = p -> next;
                p -> next = p -> next -> next;
                free( tmp );
            }
        }
    }
    
    return head;
}
```
`164 / 164 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`