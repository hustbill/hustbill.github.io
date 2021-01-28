---
title: "349--Intersection-of-Two-Arrays-2"
date: "2017-04-26"
draft: false
categories: [user-1647554-1611798760]
hiddenFromHomePage: true
---
Given two arrays, write a function to compute their intersection.
Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].  

Note:   
  * Each element in the result must be unique.    
  * The result can be in any order.  

 
[https://discuss.leetcode.com/topic/45685/three-java-solutions](https://discuss.leetcode.com/topic/45685/three-java-solutions)  

** 解题思路** 
三种解法：
1. Use two hash sets , O(n)  Time complexity  
      先把nums1加入到set中，然后用nums2中元素在set中遍历，如果set包含该元素，就加入到intersect set中。最后把intersect set 存入结果数组。

2. Sort both arrays, use two pointers   O(nlogn)  Time complexity  

3. Binary search   O(nlogn)  Time complexity  
     先sort nums2 ，然后用nums1元素在nums2中做binary search。如果能找到，就加入结果集。
