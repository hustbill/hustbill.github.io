---
title: "24. Swap Nodes in Pairs"
date: "2017-06-18 00:53:43"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Given a linked list, swap every two adjacent nodes and return its head.
For example,
Given 1->2->3->4, you should return the list as 2->1->4->3.
Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.  
** 解题思路**
Using Recursion and  Iterative Solution
 
 ```java
 // Iterative
    public ListNode swapPairs(ListNode head) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode cur  = dummy;
        
        while (cur.next != null && cur.next.next != null) {
            ListNode first = cur.next;
            ListNode second = cur.next.next;
            first.next = second.next;
            cur.next = second;
            cur.next.next = first;
            cur = cur.next.next;
            
        }
        return dummy.next;
    }

   // Recursion
    public ListNode swapPairs(ListNode head) {
      if (head == null || head.next == null) return head;
      ListNode n = head.next;
      head.next = swapPairs(head.next.next);
      n.next = head;
      return n;
    }
```
