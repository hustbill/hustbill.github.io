---
title: "349--Intersection-of-Two-Arrays-1"
date: "2017-04-26"
draft: false
categories: [user-1647554-1611798760]
hiddenFromHomePage: true
---
 [My Submissions](https://leetcode.com/problems/intersection-of-two-arrays/submissions/)

Given two arrays, write a function to compute their intersection.
**Example:**Given *nums1* = [1, 2, 2, 1]
, *nums2* = [2, 2]
, return [2]
.
**Note:**
Each element in the result must be unique.
The result can be in any order.

Hide Company Tags
 [Two Sigma](https://leetcode.com/company/two-sigma/)
Hide Tags
 [Binary Search](https://leetcode.com/tag/binary-search/) [Hash Table](https://leetcode.com/tag/hash-table/) [Two Pointers](https://leetcode.com/tag/two-pointers/) [Sort](https://leetcode.com/tag/sort/)
Hide Similar Problems
 [(E) Intersection of Two Arrays II](https://leetcode.com/problems/intersection-of-two-arrays-ii/)

```java
public class Solution {
    // https://discuss.leetcode.com/topic/45685/three-java-solutions
    
    // Time O(nlogn)  two pointers
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> set = new HashSet<>();
        Arrays.sort(nums1);
        Arrays.sort(nums2);
        
        int i = 0, j = 0;
        while ( i < nums1.length && j < nums2.length) {
            if (nums1[i] < nums2[j]) {
                i++;
            } else if (nums1[i] > nums2[j]) {
                j++;
            } else {
                set.add(nums1[i]);
                i++;
                j++;
            }
        }
        
        int[] result = new int[set.size()];
        int k = 0;
        for(Integer num : set) {
            result[k++] = num;
        }
        return result;
    }
    
    
    //Time O(n) Space O(n)
    public int[] intersection1(int[] nums1, int[] nums2) {
        Set<Integer> set = new HashSet<>();
        Set<Integer> intersect = new HashSet<>();
        
        for(int i = 0; i < nums1.length; i++) {
            set.add(nums1[i]);  
        }
        
        for (int j = 0; j < nums2.length; j++) {
            if (set.contains(nums2[j])) {
                intersect.add(nums2[j]);
            }
        }
        
        int[] result = new int[intersect.size()];
        int i = 0;
        for (int num : intersect) {
            result[i++] = num;
        }
        
        return result;
    }
}
```
