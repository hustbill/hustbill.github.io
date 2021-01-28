---
title: "21. Merge Two Sorted Lists"
date: "2017-06-10 12:06:08"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
[**Description](https://leetcode.com/problems/merge-two-sorted-lists/#/description)[**Hints](https://leetcode.com/problems/merge-two-sorted-lists/#/hints)[**Submissions](https://leetcode.com/problems/merge-two-sorted-lists/#/submissions)[**Solutions](https://leetcode.com/problems/merge-two-sorted-lists/#/solutions)

Total Accepted: **221656**
Total Submissions: **571422**
Difficulty: **Easy**
Contributor: **LeetCode**

Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.

Hide Company Tags
 [Amazon](https://leetcode.com/company/amazon/) [LinkedIn](https://leetcode.com/company/linkedin/) [Apple](https://leetcode.com/company/apple/) [Microsoft](https://leetcode.com/company/microsoft/)
Hide Tags
 [Linked List](https://leetcode.com/tag/linked-list/)
Hide Similar Problems
 [(H) Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/) [(E) Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/) [(M) Sort List](https://leetcode.com/problems/sort-list/) [(M) Shortest Word Distance II](https://leetcode.com/problems/shortest-word-distance-ii/)

** 解题思路**
recursive 递归解法。 类似merge two sorted array
  
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
      // use recursive 
      if (l2 == null)  return l1;
      if (l1 == null)  return l2;
      
      ListNode mergeHead;
      
      if (l1.val < l2.val) {
          mergeHead = l1;
          mergeHead.next = mergeTwoLists(l1.next, l2);
      } else {
          mergeHead = l2;
          mergeHead.next = mergeTwoLists(l1, l2.next);
      }
      return mergeHead;
    }
    
    public ListNode mergeTwoListsFailed(ListNode l1, ListNode l2) {
        ListNode p1 = l1;
        ListNode p2 = l2 ;
        ListNode p = new ListNode(0);
        
        
        while (p1 != null && p2 != null) {
            // p.next = (p1.val > p2.val) ? new ListNode(p1.val) : new ListNode(p2.val);
            if (p1.val > p2.val) {
                p.next = new ListNode(p1.val);
                p1 = p1.next;
            } else {
                p.next = new ListNode(p2.val);
                p2 = p2.next;
            }
         
        }
        
        while (p2 != null) {
          p.next = new ListNode(p2.val);
          p2 = p2.next;
         
        }
        
        while (p1 != null) {
            p.next = new ListNode(p1.val);
            p1 = p1.next;
          
        }
        return p;
    }
}
```
