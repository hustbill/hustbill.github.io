---
title: "404. Sum of Left Leaves"
date: "2016-10-14 14:45:06"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
[My Submissions](https://leetcode.com/problems/sum-of-left-leaves/submissions/)

Total Accepted: **11811**
Total Submissions: **25597**
Difficulty: **Easy**
Contributors: **Admin**

Find the sum of all left leaves in a given binary tree.
**Example:**
3 / \ 9 20 / \ 15 7There are two left leaves in the binary tree, with values **9** and **15** respectively. Return **24**.

Hide Company Tags
 [Facebook](https://leetcode.com/company/facebook/)
Hide Tags
 [Tree](https://leetcode.com/tag/tree/)
```java
public class Solution {
    /*Recursive method. For given node we check whether its left child is a leaf. If it is the case, we add its value to answer, otherwise recursively call method on left child. For right child we call method only if it has at least one nonnull child.
    */
    public int sumOfLeftLeaves(TreeNode root) {
        if (root == null) return 0;
        int ans = 0;
        
        if (root.left != null) { 
            if (root.left.left == null && root.left.right == null) {
                ans += root.left.val;
            } else {
                ans += sumOfLeftLeaves(root.left);
            }
        } 
        if (root.right != null) {
            ans += sumOfLeftLeaves(root.right);
        }
        return ans;
    }
}
```
