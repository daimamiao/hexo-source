---
title: 'LeetCode 328: Odd Even Linked List'
date: 2016-08-04 21:47:47
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a singly linked list, group all odd nodes together followed by the even nodes. Please note here we are talking about the node number and not the value in the nodes. <!--more-->

You should try to do it in place. The program should run in O(1) space complexity and O(nodes) time complexity.

Example:
Given `1->2->3->4->5->NULL,`
return `1->3->5->2->4->NULL.`

**Note:**
The relative order inside both the even and odd groups should remain as it was in the input. 
The first node is considered odd, the second node even and so on ...

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
struct ListNode* oddEvenList(struct ListNode* head) {
    if ( !head || !(head -> next) ){
        return head;
    }
    struct ListNode* slow = head;
    struct ListNode* fast = head -> next;
    struct ListNode* oddHead = head;
    struct ListNode* evenHead = head -> next;
    while ( fast && fast -> next ){
        slow -> next = fast -> next;
        slow = fast -> next;
        if ( !slow -> next ){
            fast -> next = NULL;
            break;
        }
        fast -> next = slow -> next;
        fast = slow -> next;
    }
    slow -> next = evenHead;
    return oddHead;
    
}
```
`70 / 70 test cases passed.`
Status: `Accepted`
Runtime: `4 ms`
