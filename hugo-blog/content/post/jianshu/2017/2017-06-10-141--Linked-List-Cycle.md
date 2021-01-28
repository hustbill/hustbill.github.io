---
title: "141. Linked List Cycle"
date: "2017-06-10 10:26:21"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---

[**Description](https://leetcode.com/problems/linked-list-cycle/#/description)[**Hints](https://leetcode.com/problems/linked-list-cycle/#/hints)[**Submissions](https://leetcode.com/problems/linked-list-cycle/#/submissions)[**Solutions](https://leetcode.com/problems/linked-list-cycle/#/solutions)

Total Accepted: **177986**
Total Submissions: **502453**
Difficulty: **Easy**
Contributor: **LeetCode**

Given a linked list, determine if it has a cycle in it.
Follow up:Can you solve it without using extra space?

Hide Company Tags
 [Amazon](https://leetcode.com/company/amazon/) [Microsoft](https://leetcode.com/company/microsoft/) [Bloomberg](https://leetcode.com/company/bloomberg/) [Yahoo](https://leetcode.com/company/yahoo/)
Hide Tags
 [Linked List](https://leetcode.com/tag/linked-list/) [Two Pointers](https://leetcode.com/tag/two-pointers/)
Hide Similar Problems
 [(M) Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)

```java
    /*
      Use two pointers, slower and faster.
        slower moves step by step. faster moves two steps at time.
        if the Linked List has a cycle slower and faster will meet at some
        point.
    */
    public boolean hasCycle(ListNode head) {
        ListNode slow = new ListNode(0);
        ListNode fast = new ListNode(0);
        slow.next = head;
        fast.next = head;
        
        while (fast != null && fast.next != null) {
            fast = fast.next.next;
            slow = slow.next;
             if (fast == slow) {
                return true;
            }
        }
        return false;
    }
```
