---
title: "19. Remove Nth Node From End of List"
date: "2017-06-17 13:12:40"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Given a linked list, remove the nth node from the end of list and return its head.

For example,

   Given linked list: 1->2->3->4->5, and n = 2.

   After removing the second node from the end, the linked list becomes 1->2->3->5.
Note:
Given n will always be valid.
Try to do this in one pass.

** 解题报告 ** 
 使用快慢指针来做。
Using  fast and slow pointers.  
(1)  Move one pointer fast --> n+1 places forward, to maintain a gap of n between the two pointers 
(2) and then move both at the same speed. 
(3) Finally, when the fast pointer reaches the end, the slow pointer will be n+1 places behind - just the right spot for it to be able to skip the next node.

Since the question gives that n is valid, not too many checks have to be put in place. Otherwise, this would be necessary.

```java
    public ListNode removeNthFromEnd(ListNode head, int n) {
      ListNode start = new ListNode(0);
      start.next = head;
      ListNode fast = start;
      ListNode slow = start;
      
      // Move fast in front so that the gap between fast and slow becomes n;
      for(int i = 1; i <= n + 1; i++) {
          fast = fast.next;
      }
      // Moving fast to the end, maintaining the gap
      while(fast != null) {
          fast = fast.next;
          slow = slow.next;
      }
      
      // Skip the desired node
      slow.next = slow.next.next;
      return start.next;
    }

```
