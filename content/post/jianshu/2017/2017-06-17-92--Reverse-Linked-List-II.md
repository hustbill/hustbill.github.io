---
title: "92. Reverse Linked List II"
date: "2017-06-17 11:45:51"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Reverse a linked list from position m to n. Do it in-place and in one-pass.

For example:
Given 1->2->3->4->5->NULL, m = 2 and n = 4,

return 1->4->3->2->5->NULL.

Note:
Given m, n satisfy the following condition:
1 ≤ m ≤ n ≤ length of list.


** 解题思路 ** 
先用dummy node来记录链表的起始点， 再找到第m个节点- start， 和它后续的节点 then， 然后用pre， start ， then 在for 循环中实现（m-n）子链表的反转即可。

Simply just reverse the list along the way using 4 pointers: dummy, pre, start, then
[参考: reverse using 4 pointers](https://discuss.leetcode.com/topic/8976/simple-java-solution-with-clear-explanation)  

```java
    public ListNode reverseBetween(ListNode head, int m, int n) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;  // create the dummy node to mark the head of this list
        
        ListNode pre = dummy;  // make a pointer pre as a marker for the node before reversing
        for (int i = 0; i < m - 1; i++) {
            pre = pre.next;
        }
        
        ListNode start = pre.next;    // a pointer to the beginning of a sub-list that will be reversed
        ListNode then = start.next; // a pointer to the node will be reversed
        
        // 1->2->3->4->5; m = 2; n = 4  ---> pre = 1, start = 2, then = 3
        // dummy -> 1 ->2 ->3 ->4 ->5
        for (int i = 0 ; i < n - m; i++) {
            start.next = then.next;
            then.next = pre.next;
            pre.next = then;
            then = start.next;
        }
        // first reversing : dummy->1 - 3 - 2 - 4 - 5; pre = 1, start = 2, then = 4
        // second reversing: dummy->1 - 4 - 3 - 2 - 5; pre = 1, start = 2, then = 5 (finish)
        return dummy.next;
    }
```
