---
title: "169. Majority Element"
date: "2017-06-12 15:47:10"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
[**Description](https://leetcode.com/problems/majority-element/#/description)[**Hints](https://leetcode.com/problems/majority-element/#/hints)[**Submissions](https://leetcode.com/problems/majority-element/#/submissions)[**Solutions](https://leetcode.com/problems/majority-element/#/solutions)

Total Accepted: **192332**
Total Submissions: **417285**
Difficulty: **Easy**
Contributor: **LeetCode**

Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** ⌊ n/2 ⌋
 times.
You may assume that the array is non-empty and the majority element always exist in the array.
**Credits:**Special thanks to [@ts](https://oj.leetcode.com/discuss/user/ts) for adding this problem and creating all test cases.

Hide Company Tags
 [Adobe](https://leetcode.com/company/adobe/) [Zenefits](https://leetcode.com/company/zenefits/)
Hide Tags
 [Array](https://leetcode.com/tag/array/) [Divide and Conquer](https://leetcode.com/tag/divide-and-conquer/) [Bit Manipulation](https://leetcode.com/tag/bit-manipulation/)
Hide Similar Problems
 [(M) Majority Element II](https://leetcode.com/problems/majority-element-ii/)

```java
public class Solution {
    // O(n) time O(1) space fastest solution
    public int majorityElement(int[] nums) {
        int major = nums[0], count = 1;
        for (int i = 1; i < nums.length; i++) {
            if (count == 0) {
                count++;
                major = nums[i];
            } else if (major == nums[i]) {
                count++;
            } else {
                count--;
            }
        }
        return major;
    }
    
    public int majorityElementFailed(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for (int n : nums) {
            set.add(n);
        }
        int max = -1;
        
        int[] countList = new int[nums.length];
        
        for (int k : set) {
           for (int i = 0; i < nums.length; i++) {
               if (nums[i] == k) countList[i]++;
           }
        }
        return max;
    }
}
```
