---
title: "219. Contains Duplicate II"
date: "2016-12-18 03:22:26"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
 [My Submissions](https://leetcode.com/problems/contains-duplicate-ii/submissions/)

Total Accepted: **88264**
Total Submissions: **281930**
Difficulty: **Easy**
Contributors: **Admin**

Given an array of integers and an integer *k*, find out whether there are two distinct indices *i* and *j* in the array such that **nums[i] = nums[j]** and the difference between *i* and *j* is at most *k*.

Hide Company Tags
 [Palantir](https://leetcode.com/company/palantir/) [Airbnb](https://leetcode.com/company/airbnb/)
Hide Tags
 [Array](https://leetcode.com/tag/array/) [Hash Table](https://leetcode.com/tag/hash-table/)
Hide Similar Problems
 [(E) Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) [(M) Contains Duplicate III](https://leetcode.com/problems/contains-duplicate-iii/)

**Explanation:**   
It iterates over the array using a sliding window. The front of the window is at i, the rear of the window is k steps back. The elements within that window are maintained using a set. While adding new element to the set, if add() returns false, it means the element already exists in the set. At that point, we return true. If the control reaches out of for loop, it means that inner return true never executed, meaning no such duplicate element was found.  

[Reference - simple-java-solution]( https://discuss.leetcode.com/topic/15305/simple-java-solution/6)

```java
    // https://discuss.leetcode.com/topic/15305/simple-java-solution/6
    public boolean containsNearbyDuplicate(int[] nums, int k) {
      Set<Integer> set = new HashSet<Integer>();
      for (int i = 0; i < nums.length; i++) {
          if (i > k) set.remove(nums[i - k - 1]);
          if (!set.add(nums[i])) return true;
      }
      return false;
    }
```
