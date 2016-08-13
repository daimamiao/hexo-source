---
title: 'LeetCode 86: Partition List'
date: 2016-08-05 11:27:08
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.<!--more-->You should preserve the original relative order of the nodes in each of the two partitions. 
For example,Given `1->4->3->2->5->2` and `x = 3`,return `1->2->2->4->3->5`.
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
struct ListNode* partition(struct ListNode* head, int x) {
    if ( !head ) {
        return NULL;
    }
    struct ListNode *smaller, *smallerHeader;
    smallerHeader -> next = head;
    smaller = smallerHeader;
    struct ListNode *bigger, *biggerHeader;
    biggerHeader -> next = head;
    bigger = biggerHeader;
    while ( head ) {
        if ( head -> val < x ) {
            smaller -> next = head;
            smaller = head;
        }else {
            bigger -> next = head;
            bigger = head;
        }
        head = head -> next;
    }
    bigger -> next = NULL;
    smaller -> next = biggerHeader -> next;
    return smallerHeader -> next;
}
```
`166 / 166 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`