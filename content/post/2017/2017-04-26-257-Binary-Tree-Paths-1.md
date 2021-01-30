---
title: "257--Binary-Tree-Paths-1"
date: "2017-04-26"
draft: false
categories: [leetcode]
hiddenFromHomePage: true
---
Given a binary tree, return all root-to-leaf paths.

For example, given the following binary tree:
```code 
   1
 /   \
2     3
 \
  5
```
All root-to-leaf paths are:

["1->2->5", "1->3"]
   
## 解题分析  
The time complexity for the problem should be O(n), since we are basically visiting each node in the tree. Yet an interviewer might ask you for further optimization when he or she saw a string concatenation. A string concatenation is just too costly. A StringBuilder can be used although a bit tricky since it is not immutable like string is.

When using StringBuilder, We can just keep track of the length of the StringBuilder before we append anything to it before recursion and afterwards set the length back. Another trick is when to append the "->", since we don't need the last arrow at the end of the string, we only append it before recurse to the next level of the tree. Hope the solution helps!

```java
// https://discuss.leetcode.com/topic/21474/accepted-java-simple-solution-in-8-lines/13
 public List<String> binaryTreePaths(TreeNode root) {
        List<String> res = new ArrayList<>();
        StringBuilder sb = new StringBuilder();
        helper(res, root, sb);
        return res;
    }
    
    private void helper(List<String> res, TreeNode root, StringBuilder sb) {
        if(root == null) {
            return;
        }
        int len = sb.length();
        sb.append(root.val);
        if(root.left == null && root.right == null) {
            res.add(sb.toString());
        } else {
            sb.append("->");
            helper(res, root.left, sb);
            helper(res, root.right, sb);
        }
        sb.setLength(len);
    }
```
