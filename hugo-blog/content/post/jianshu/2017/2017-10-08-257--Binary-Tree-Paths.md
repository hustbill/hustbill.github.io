---
title: "257. Binary Tree Paths"
date: "2017-10-08 23:50:01"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
** Notes:
这道题和 PathSum ii  比较类似，解法只需要改动一两行即可。
**Add to List

[**Description](https://leetcode.com/problems/binary-tree-paths/#/description)[**Hints](https://leetcode.com/problems/binary-tree-paths/#/hints)[**Submissions](https://leetcode.com/problems/binary-tree-paths/#/submissions)[**Solutions](https://leetcode.com/problems/binary-tree-paths/#/solutions)

Total Accepted: **101944**
Total Submissions: **276629**
Difficulty: **Easy**
Contributor: **LeetCode**

Given a binary tree, return all root-to-leaf paths.
For example, given the following binary tree:

1 / \2 3 \ 5

All root-to-leaf paths are:
["1->2->5", "1->3"]

**Credits:**Special thanks to [@jianchao.li.fighter](https://leetcode.com/discuss/user/jianchao.li.fighter) for adding this problem and creating all test cases.

Hide Company Tags
 [Google](https://leetcode.com/company/google/) [Apple](https://leetcode.com/company/apple/) [Facebook](https://leetcode.com/company/facebook/)
Hide Tags
 [Tree](https://leetcode.com/tag/tree/) [Depth-first Search](https://leetcode.com/tag/depth-first-search/)
Hide Similar Problems
 [(M) Path Sum II](https://leetcode.com/problems/path-sum-ii/)
```java
    public List<String> binaryTreePaths(TreeNode root) {
        List<String> res = new ArrayList<>();
        String cur = "";
        dfs(root, res, cur);
        return res;
    }
    
    private void dfs(TreeNode root, List<String> res, String cur) {
        if (root == null) {
            return ;
        }
        
        if (cur == "") {
          cur = cur + String.valueOf(root.val);
        } else {
          cur = cur + "->" + String.valueOf(root.val);    
        }
        
        if (root.left == null && root.right == null) {
            res.add(cur);
        }
        dfs(root.left, res, cur);
        dfs(root.right, res, cur);
        cur = cur.substring(0, cur.length() -1);
    }
```
