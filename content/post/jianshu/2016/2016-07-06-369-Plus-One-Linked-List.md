---
title: "369. Plus One Linked List"
date: "2016-07-06 11:35:24"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
369- Plus One Linked List
 **Question
Editorial Solution

 [My Submissions](https://leetcode.com/problems/plus-one-linked-list/submissions/)

Total Accepted: **1189**
Total Submissions: **2373**
Difficulty: **Medium**

Given a non-negative number represented as a singly linked list of digits, plus one to the number.
The digits are stored such that the most significant digit is at the head of the list.
**Example:**
Input:1->2->3Output:1->2->4

Hide Company Tags
 [Google](https://leetcode.com/company/google/)
Hide Tags
 [Linked List](https://leetcode.com/tag/linked-list/)
Hide Similar Problems
 [(E) Plus One](https://leetcode.com/problems/plus-one/)
```java

 public ListNode plusOne(ListNode head) {
  /*
   * At the first glance, I want to reverse the inputs, add one, then
   * reverse back. But that is too intuitive and I don't think this is an
   * expected solution. Then what kind of alg would adding one in reverse
   * way for list?
   * 
   * Recursion! With recursion, we can visit list in reverse way! So here is my
   * recursive solution.
   * https://discuss.leetcode.com/topic/49541/java-recursive-solution
   */
  if (dfs(head) == 0) {
   return head;
  } else {
   ListNode newHead = new ListNode(1);
   newHead.next = head;
   return newHead;
  }
 }

 // Recursion solution
 public int dfs(ListNode head) {
  if (head == null)
   return 1;

  int carry = dfs(head.next);
  if (carry == 0)
   return 0;

  int val = head.val + 1;
  head.val = val % 10;
  return val / 10;
 }
```
