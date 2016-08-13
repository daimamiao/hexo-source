---
title: 'LeetCode 2: Add Two Numbers'
date: 2016-08-05 16:52:42
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
You are given two linked lists representing two non-negative numbers. The digits are stored in reverse order and each of their nodes contain a single digit. <!--more--> Add the two numbers and return it as a linked list.

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
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
struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2) {
    struct ListNode* c1 = l1;
    struct ListNode* c2 = l2;
    struct ListNode* sentinel = (struct ListNode*)malloc(sizeof(struct ListNode));
    struct ListNode* dummy = sentinel;
    int sum = 0;
    while ( c1 || c2) {
        sum /= 10;
        if ( c1 ){
            sum += c1 -> val;
            c1 = c1 -> next;
        }
        if ( c2 ){
            sum += c2 -> val;
            c2 = c2 -> next;
        }
        dummy -> next = (struct ListNode*)malloc(sizeof(struct ListNode));
        dummy -> next -> val = sum % 10;
        dummy = dummy -> next;
    }
    if ( sum / 10 == 1 ) {
        dummy -> next = (struct ListNode*)malloc(sizeof(struct ListNode));
        dummy -> next -> val = 1;
    }
    
    return sentinel -> next;
}
```

C++版本：
```java
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
       ListNode preheader(-1), *curr=&preheader;
        int carry=0;
        while(l1 || l2 || carry) {
            curr->next = new ListNode(((l1?l1->val:0)+(l2?l2->val:0)+carry)%10);
            curr = curr->next;
            carry = ((l1?l1->val:0)+(l2?l2->val:0)+carry)/10;
            l1?l1=l1->next:0;
            l2?l2=l2->next:0;
        }
        return preheader.next;
    }
};
```

`1558 / 1558 test cases passed.`
`Status: Accepted`
Runtime: `40 ms`