---
title: "86. Partition List"
date: "2017-06-18 02:52:30"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.

You should preserve the original relative order of the nodes in each of the two partitions.

For example,
Given 1->4->3->2->5->2 and x = 3,
return 1->2->2->4->3->5.

** 解题思路** 
用两个queue 来分别存放  val < x  和 val >=x 的node， 然后把这两个node 连起来即可。 
注意，要把第二个queue的尾巴设置为null，避免循环。
the basic idea is to maintain two queues, the first one stores all nodes with val less than x, and the second queue stores all the rest nodes. Then concat these two queues.
 Remember to set the tail of second queue a null next, otherwise you will get TLE.  

```java
/* the basic idea is to maintain two queues, the first one stores all nodes with val less than x, and the second queue stores all the rest nodes. Then concat these two queues.
 Remember to set the tail of second queue a null next, otherwise you will get TLE.
 */
public class Solution {
    public ListNode partition(ListNode head, int x) {
        ListNode dummy1 = new ListNode(0);  //dummy heads of the 1st and 2nd queues
        ListNode dummy2 = new ListNode(0);  //current tails of the two queues;
        ListNode curr1 = dummy1;
        ListNode curr2 = dummy2;
        
        while (head != null) {
            if (head.val < x) {
                curr1.next = head;
                curr1 = head;
            } else {
                curr2.next = head;
                curr2 = head;
            }
            head = head.next;
        }
        curr2.next = null;  //important! avoid cycle in linked list. otherwise u will get TLE.
        curr1.next = dummy2.next;
        return dummy1.next;
    }
    // 失败的
    public ListNode partitionFailed(ListNode head, int x) {
      ListNode dummy = new ListNode(0);
      dummy.next = head;
      ListNode pre = dummy;
      while (pre.next != null && pre.next.next != null) {
          ListNode first = pre.next;
          ListNode second = pre.next.next;
          if (first.val >= x && second.val < x) {
              first.next = second.next;
              pre.next = second;
              pre.next.next = first;
              pre = pre.next.next;
          }
          pre = pre.next.next;
      }
      return dummy.next;
    }
```
