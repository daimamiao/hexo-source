---
title: 'LeetCode 24: Swap Nodes in Pairs'
date: 2016-08-02 17:17:28
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a linked list, swap every two adjacent nodes and return its head. For example, Given `1->2->3->4`, you should return the list as `2->1->4->3`.<!--more-->
Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.
### 题意
考虑一个单链表， 交换每两个相邻的节点并返回头节点。比如，给出`1->2->3->4`，你应该返回`2->1->4->3`。
### 思路
题目意思是给定一个单链表，交换两个相邻的节点。我的做法是先找到新链表的头结点，然后像交换两个变量的值的方式，来交换两个相邻的节点，这里需要注意的是，交换的时候，需要保存交换节点的前后节点，这里我用left、right去保存，为了交换之后，前后节点不丢失。
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
struct ListNode* swapPairs(struct ListNode* head) {
    struct ListNode *p, *q, *right, *left;
    struct ListNode * ret;

    if(!head || !head->next)
        return head;

    p = head;
    q = p->next;

    if(p && q)
        ret = q;

    while(p && q)
    {
        right = q->next;
        q->next = p;
        left = p;
        p->next = right;
        p = right;

        if(!right || !right->next)
            break;

        if(right->next)
        {
            q = p->next;
            left->next = q;
        }
    }

    return ret;
}
```