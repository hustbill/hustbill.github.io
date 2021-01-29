---
title: "350. Intersection of Two Arrays II"
date: "2017-06-12 04:58:47"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Given two arrays, write a function to compute their intersection.
Example:
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2, 2].
Note:
Each element in the result should appear as many times as it shows in both arrays.

The result can be in any order.

** Follow up: **   
What if the given array is already sorted? How would you optimize your algorithm?

What if nums1's size is small compared to nums2's size? Which algorithm is better?

What if elements of nums2 are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?

 ** 解题思路** 
这一题比较有意思。 Follow up三个问题，需要考虑两个array的大小。第三问 参考这两个分析：
[第三问分析之一:](https://discuss.leetcode.com/topic/45992/solution-to-3rd-follow-up-question/2)  
- If only nums2 cannot fit in memory, put all elements of nums1 into a HashMap, read chunks of array that fit into the memory, and record the intersections.

- If both nums1 and nums2 are so huge that neither fit into the memory, sort them individually (external sort), then read 2 elements from each array at a time in memory, record intersections.

[第三问分析之二 补充：](https://discuss.leetcode.com/topic/45992/solution-to-3rd-follow-up-question/4)  
 
Thanks for the solution. I think the second part of the solution is impractical, if you read 2 elements at a time, this procedure will take forever. In principle, we want minimize the number of disk access during the run-time.
An improvement can be sort them using external sort, read (let's say) 2G of each into memory and then using the 2 pointer technique, then read 2G more from the array that has been exhausted. Repeat this until no more data to read from disk.
But I am not sure this solution is good enough for an interview setting. Maybe the interviewer is expecting some solution using Map-Reduce paradigm.
** 参考代码** 

 ```java
 
    /* Sort both arrays, use two pointers
       Arrays.sort(nums1); Arrays.sort(nums2);
       Test case: 
        [2,1]
        [1,1] -> [1]
    */
    public int[] intersect(int[] nums1, int[] nums2) {
        List<Integer> list = new ArrayList<>();
        Arrays.sort(nums1);
        Arrays.sort(nums2);
        int i = 0, j = 0;
        while(i < nums1.length &&  j < nums2.length) {
            if (nums1[i] > nums2[j]) {
                j++;
            } else if (nums1[i] < nums2[j]) {
                i++;
            } else {
              list.add(nums1[i]);
              i++;
              j++;
            }
        }
        int[] res = new int[list.size()];
        int k = 0;
        for (Integer e : list) {
            res[k++] = e;
        }
        return res;
    }
```
