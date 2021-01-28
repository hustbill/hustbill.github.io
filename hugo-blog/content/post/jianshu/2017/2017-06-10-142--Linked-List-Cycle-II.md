---
title: "142. Linked List Cycle II"
date: "2017-06-10 10:51:44"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
[**Description](https://leetcode.com/problems/linked-list-cycle-ii/#/description)[**Hints](https://leetcode.com/problems/linked-list-cycle-ii/#/hints)[**Submissions](https://leetcode.com/problems/linked-list-cycle-ii/#/submissions)[**Solutions](https://leetcode.com/problems/linked-list-cycle-ii/#/solutions)

Total Accepted: **112637**
Total Submissions: **363331**
Difficulty: **Medium**
Contributor: **LeetCode**

Given a linked list, return the node where the cycle begins. If there is no cycle, return null
.
**Note:** Do not modify the linked list.
**Follow up**:Can you solve it without using extra space?

Hide Tags
 [Linked List](https://leetcode.com/tag/linked-list/) [Two Pointers](https://leetcode.com/tag/two-pointers/)
Hide Similar Problems
 [(E) Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/) [(M) Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)

** 解题思路 **
用快慢指针，快指针一次走两步，慢指针一次走一步，来先确定是否有cycle。  
如果存在cycle，则将fast = head，再重新 fast =fast.next, slow = slow.next 两个指针都单步走，找到fast = slow点即可确定cycle起始点。
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode detectCycle(ListNode head) {
        if (head == null || head.next == null) return null;
        
        ListNode slow = head;
        ListNode fast = head;
        boolean isCycle = false;
        
        while (fast != null && fast.next != null) {
            fast = fast.next.next;
            slow = slow.next;
            if (fast == slow) {
                isCycle = true;
                break; // don't forget to break the loop
            }
        }
        if (!isCycle) return null;
        
        // find the node while cycle begins
        fast = head;
        while (fast != slow) {
            fast = fast.next;
            slow = slow.next;
        }
        
        return slow;
    }
}
```
