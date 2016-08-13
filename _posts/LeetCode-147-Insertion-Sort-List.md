---
title: 'LeetCode 147: Insertion Sort List'
date: 2016-08-05 14:22:38
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Sort a linked list using insertion sort. <!--more-->

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
struct ListNode* insertionSortList(struct ListNode* head) {
    if ( !head ) {
        return head;
    }
    struct ListNode* helper;
    helper -> next = NULL;
    struct ListNode* cur = head;
    struct ListNode* behind = NULL;
    struct ListNode* pre = helper;
    while ( cur ) {
        behind = cur -> next;
        while ( pre -> next && pre->next->val < cur->val ) {
            pre = pre -> next;
        }
        
        cur -> next = pre -> next;
        pre -> next = cur;
        pre = helper;
        cur = behind;
    }
    return helper -> next;
}
```
`21 / 21 test cases passed.`
Status: `Accepted`
Runtime: `64 ms`