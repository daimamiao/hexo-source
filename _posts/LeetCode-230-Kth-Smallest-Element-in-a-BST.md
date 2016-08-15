---
title: 'LeetCode 230:Kth Smallest Element in a BST'
date: 2016-08-14 07:43:32
tags: [LeetCode, Binary Search]
categories: LeetCode
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given a binary search tree, write a function kthSmallest to find the kth smallest element in it. <!--more-->

**Note:**
You may assume k is always valid, 1 ≤ k ≤ BST's total elements.

**Follow up:**
What if the BST is modified (insert/delete operations) often and you need to find the kth smallest frequently? How would you optimize the kthSmallest routine?

### Code
```c
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
int countNodes(struct TreeNode* root) {
    if (root == NULL) {
        return 0;
    }
    return 1 + countNodes(root -> left) + countNodes(root -> right);
}
int kthSmallest(struct TreeNode* root, int k) {
    int count = countNodes(root -> left);
    if (k <= count) {
        return kthSmallest(root -> left, k);
    } else if (k > count + 1) {
        return kthSmallest(root -> right, k - count - 1);
    }
    return root -> val;
}
```