---
title: 'LeetCode 234: Palindrome Linked List'
date: 2016-08-03 22:21:55
tags: [LeetCode, Linked List]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a singly linked list, determine if it is a palindrome. Follow up: Could you do it in O(n) time and O(1) space? <!--more-->
### 思路
这道题让我们判断一个链表是否为回文链表，LeetCode中关于回文串的题共有六道，除了这道，其他的五道为 Palindrome Number 验证回文数字， Validate Palindrome 验证回文字符串， Palindrome Partitioning 拆分回文串，Palindrome Partitioning II 拆分回文串之二 和 Longest Palindromic Substring 最长回文串.链表比字符串难的地方就在于不能通过坐标来直接访问，而只能从头开始遍历到某个位置。那么根据回文串的特点，我们需要比较对应位置的值是否相等，那么我们首先需要找到链表的中点，这个可以用快慢指针来实现，使用方法可以参见之前的两篇Convert Sorted List to Binary Search Tree 将有序链表转为二叉搜索树 和 Reorder List 链表重排序，我们使用快慢指针找中点的原理是fast和slow两个指针，每次快指针走两步，慢指针走一步，等快指针走完时，慢指针的位置就是中点。我们还需要用栈，每次慢指针走一步，都把值存入栈中，等到达中点时，链表的前半段都存入栈中了，由于栈的后进先出的性质，就可以和后半段链表按照回文对应的顺序比较了。
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
struct ListNode* reverseList(struct ListNode* head) {
    if (NULL == head){
        return head;
    }
    struct ListNode *p = head;
    struct ListNode *pNext;
    p = head->next;
    head->next = NULL;
    while (p != NULL){
        pNext = p->next;
        p->next = head;
        head = p;
        p = pNext;
    }
    return head;
}
bool isPalindrome(struct ListNode* head) {
    struct ListNode* fast = head;
    struct ListNode* slow = head;
    while ( fast != NULL && fast->next != NULL) {
        slow = slow -> next;
        fast = fast -> next -> next;
    }
    ///reverse the bottom half list
    struct ListNode* rHead = reverseList(slow);
    while(head != NULL && rHead != NULL){
        if(head->val != rHead->val)
            return false;
        head = head->next;
        rHead = rHead->next;
    }
    return true;
}
```
`22 / 22 test cases passed.`
Status: `Accepted`
Runtime: `12 ms`