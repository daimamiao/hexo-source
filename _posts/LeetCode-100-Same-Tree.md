---
title: 'LeetCode 100: Same Tree'
date: 2016-08-11 09:21:44
categories: LeetCode
tags: [LeetCode, Tree]
thumbnail: http://7xveyh.com1.z0.glb.clouddn.com/logolarge.jpg
---
Given two binary trees, write a function to check if they are equal or not. Two binary trees are considered equal if they are structurally identical and the nodes have the same value. <!--more-->

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
bool isSameTree(struct TreeNode* p, struct TreeNode* q) {
    if (p == NULL && q == NULL) {
        return 1;
    } else if (p == NULL || q == NULL) {
        return 0;
    } else {
        if (p -> val == q -> val) {
            return isSameTree(p -> left, q -> left) && isSameTree(p -> right, q -> right);
        }
        return 0;
    }
}
```

