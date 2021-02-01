---
title: "234. Palindrome Linked List"
date: "2016-05-03 14:22:01"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Given a singly linked list, determine if it is a palindrome.

Follow up:
Could you do it in O(n) time and O(1) space?

** 解题思路 **
（1）用快慢指针找到中点
（2）然后把右边那一半反转。
（3）再依次比较左右两边，如果不相等，则返回false； 若左右两边对称相等，则返回true， 即这个链表是回文链表。  

This can be solved by reversing the 2nd half and compare the two halves. Let's start with an example [1, 1, 2, 1].
``` code
In the beginning, set two pointers fast and slow starting at the head.

1 -> 1 -> 2 -> 1 -> null 
sf
(1) Move: fast pointer goes to the end, and slow goes to the middle.

1 -> 1 -> 2 -> 1 -> null 
          s          f
(2) Reverse: the right half is reversed, and slow pointer becomes the 2nd head.

1 -> 1    null <- 2 <- 1           
h                      s
(3) Compare: run the two pointers head and slow together and compare.

1 -> 1    null <- 2 <- 1             
     h            s 
```
** 参考代码  ** 
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class IsPalindrome_234 {
    public boolean isPalindrome(ListNode head) {
        // ref" https://leetcode.com/discuss/45656/easy-understand-java-solution-o-1-space-cost
        if(head == null) {
                   return true;
               }
               ListNode p1 = head;
               ListNode p2 = head;
               ListNode p3 = p1.next;
               ListNode pre = p1;
               //find mid pointer, and reverse head half part
               while(p2.next != null && p2.next.next != null) {
                   p2 = p2.next.next;
                   pre = p1;
                   p1 = p3;
                   p3 = p3.next;
                   p1.next = pre;
               }

               //odd number of elements, need left move p1 one step
               if(p2.next == null) {
                   p1 = p1.next;
               }
               else {   //even number of elements, do nothing

               }
               //compare from mid to head/tail
               while(p3 != null) {
                   if(p1.val != p3.val) {
                       return false;
                   }
                   p1 = p1.next;
                   p3 = p3.next;
               }
               return true;

           }
    }
}
```
