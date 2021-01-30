---
title: "108. Convert Sorted Array to Binary Search Tree"
date: "2017-09-18 09:22:58"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Given an array where elements are sorted in ascending order, convert it to a height balanced BST.  
解题思路：  dfs ，按照bst的定义，从nums的中点选做head， 然后左右两边去dfs  

```java
 public TreeNode sortedArrayToBST(int[] nums) {
      if (nums.length == 0) {
          return null;
      }
      TreeNode head = helper(nums, 0, nums.length - 1);
      return head;
    }
    public TreeNode helper(int[] nums, int low, int high) {
        if (low > high) { // Done
            return null;
        }
        int mid = (low + high) /2;
        TreeNode node = new TreeNode(nums[mid]);
        node.left = helper(nums, low, mid - 1);
        node.right = helper(nums, mid + 1, high);
        return node;
    }
```
