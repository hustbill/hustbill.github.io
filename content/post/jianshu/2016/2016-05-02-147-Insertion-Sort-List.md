---
title: "147. Insertion Sort List"
date: "2016-05-02 08:31:04"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
147. Insertion Sort List
   **[My Submissions](https://leetcode.com/problems/insertion-sort-list/submissions/)Question
Editorial Solution

Total Accepted: **70024** Total Submissions: **238256** Difficulty: **Medium**

Sort a linked list using insertion sort.

Hide Tags
 [Linked List](https://leetcode.com/tag/linked-list/) [Sort](https://leetcode.com/tag/sort/)
Hide Similar Problems
 [(M) Sort List](https://leetcode.com/problems/sort-list/)

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
    public ListNode insertionSortList(ListNode head) {
        if (head == null)  {
            return head;
        }
        // Ref : https://leetcode.com/discuss/24663/an-easy-and-clear-way-to-sort-o-1-space
        ListNode helper = new ListNode(0); // new starter of the sroted list 
        ListNode cur = head; // the node will be inserted
        
        ListNode pre = helper; // insert node betweeen pre and pre.next
        ListNode next = null;  // the next ndoe will be inserted
        
        // not the end of input list
        while (cur != null) {
            next = cur.next;  //3
            // find the right place to insert
            while (pre.next != null && pre.next.val < cur.val) {
                pre = pre.next;
            }
            // insert between pre and pre.next
            cur.next = pre.next;
            pre.next = cur;  //1
            pre = helper;
            cur = next; //3
        }
        return helper.next;
    }
}
```
