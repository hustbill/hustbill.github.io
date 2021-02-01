---
title: " 23. Merge k Sorted Lists"
date: "2016-12-24 13:39:02"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
 [My Submissions](https://leetcode.com/problems/merge-k-sorted-lists/submissions/)

Total Accepted: **121007**
Total Submissions: **469882**
Difficulty: **Hard**
Contributors: **Admin**

Merge *k* sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

Hide Company Tags
 [LinkedIn](https://leetcode.com/company/linkedin/) [Google](https://leetcode.com/company/google/) [Uber](https://leetcode.com/company/uber/) [Airbnb](https://leetcode.com/company/airbnb/) [Facebook](https://leetcode.com/company/facebook/) [Twitter](https://leetcode.com/company/twitter/) [Amazon](https://leetcode.com/company/amazon/) [Microsoft](https://leetcode.com/company/microsoft/)
Hide Tags
 [Divide and Conquer](https://leetcode.com/tag/divide-and-conquer/) [Linked List](https://leetcode.com/tag/linked-list/) [Heap](https://leetcode.com/tag/heap/)
Hide Similar Problems
 [(E) Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) [(M) Ugly Number II](https://leetcode.com/problems/ugly-number-ii/)

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
    public ListNode mergeKLists(ListNode[] lists) {
      return partition(lists, 0, lists.length - 1);
    }
    
    public ListNode partition(ListNode[] lists, int s, int e) {
        if (s == e) return lists[s];
        
        if (s < e) {
            int m = (s + e) / 2;
            ListNode l1 = partition(lists, s, m);
            ListNode l2 = partition(lists, m + 1, e);
            return merge(l1, l2);
        } else {
            return null;
        }
    }
    
    public ListNode merge(ListNode l1, ListNode l2) {
        ListNode res = new ListNode(0);
        ListNode p = res;
        
        if (l1 == null) return l2;
        if (l2 == null) return l1;
        
        while (l1 != null && l2 != null) {
            if (l1.val < l2.val) {
                p.next = new ListNode(l1.val);
                l1 = l1.next;
            } else {
                p.next = new ListNode(l2.val);
                l2 = l2.next;
            }
            p = p.next;
        }
        
        if (l1 != null) p.next = l1;
        if (l2 != null) p.next = l2;
        return res.next;
    }
}
```
