---
title: 'LeetCode 203: Remove Linked List Elements'
date: 2016-08-02 22:58:14
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Remove all elements from a linked list of integers that have value val. Example Given: `1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6`, val = 6. Return: `1 --> 2 --> 3 --> 4 --> 5`. <!--more-->
### 思路
两个指针, 一样的就删, 不一样就next.
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
struct ListNode* removeElements(struct ListNode* head, int val) {
    struct ListNode* dummy;
    dummy -> next = head;
    struct ListNode* p = dummy;  
    struct ListNode* q = head;
    while(q != NULL) {  
        if(q->val == val) {  
            p->next = q->next;  
        } else {  
            p = p->next;  
        }  
        q = q->next;  
    }  
          
    return dummy->next; 
}
```
`63 / 63 test cases passed.`
Status: `Accepted`
Runtime: `12 ms`

```flow
st=>start: Start
e=>end
op=>operation: My Operation
cond=>condition: Yes or No?

st->op->cond
cond(yes)->e
cond(no)->op
```
```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```