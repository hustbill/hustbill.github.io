---
title: "606. Construct String from Binary Tree"
date: "2017-07-05 01:53:37"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
You need to construct a string consists of parenthesis and integers from a binary tree with the preorder traversing way.

The null node needs to be represented by empty parenthesis pair "()". And you need to omit all the empty parenthesis pairs that don't affect the one-to-one mapping relationship between the string and the original binary tree.

Example 1:
Input: Binary tree: [1,2,3,4]
       1
     /   \
    2     3
   /    
  4     

Output: "1(2(4))(3)"

Explanation: Originallay it needs to be "1(2(4)())(3()())", 
but you need to omit all the unnecessary empty parenthesis pairs. 
And it will be "1(2(4))(3)".
Example 2:
Input: Binary tree: [1,2,3,null,4]
       1
     /   \
    2     3
     \  
      4 

Output: "1(2()(4))(3)"

Explanation: Almost the same as the first example, 
except we can't omit the first parenthesis pair to break the one-to-one mapping relationship between the input and the output.

**解题思路**
Here is my recursive solution. If the left child is null , add "()" to result string. 

```java
    public String tree2str(TreeNode t) {
        String res = "";
        if (t == null) return res;
        
        res += t.val;
        if (t.left == null && t.right != null) res += "()";  // left subtree is null , add "()"
        
        if (t.left != null) res += "(" + tree2str(t.left) + ")";
        if (t.right != null) res += "(" + tree2str(t.right) + ")";
        
        return  res;
    }

```
