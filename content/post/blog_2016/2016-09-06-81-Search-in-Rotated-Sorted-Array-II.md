---
title: "81. Search in Rotated Sorted Array II"
date: "2016-09-06 01:56:54"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
81- Search in Rotated Sorted Array II
 **Question
Editorial Solution

 [My Submissions](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/submissions/)

Total Accepted: **71935**
Total Submissions: **221320**
Difficulty: **Medium**

Follow up for "Search in Rotated Sorted Array":What if *duplicates* are allowed?
Would this affect the run-time complexity? How and why?
Write a function to determine if a given target is in the array.
** 解题思路**
    test case
    [1,1,3,1]  3
    [1,3, 1, 1, 1] 3  
 关键在于处理duplicates。
If we get nums[start] == nums[mid] == nums[end], then shifting out any of the two sides won't change the result but can help remove duplicate from consideration, here we just use left++ but end-- works too
```java
 public boolean search(int[] nums, int target) {
        int start  = 0, end = nums.length - 1;
        
        //check each num so we will check start == end
        //We always get a sorted part and a half part
        //we can check sorted part to decide where to go next
        while(start <= end){
            int mid = start + (end - start)/2;
            if(nums[mid] == target) return true;
            
            //if left part is sorted
            if(nums[start] < nums[mid]){
                if(target < nums[start] || target > nums[mid]){
                    //target is in rotated part
                    start = mid + 1;
                }else{
                    end = mid - 1;
                }
            }else if(nums[start] > nums[mid]){
                //right part is rotated
                
                //target is in rotated part
                if(target < nums[mid] || target > nums[end]){
                    end = mid -1;
                }else{
                    start = mid + 1;
                }
            }else{
                //duplicates, we know nums[mid] != target, so nums[start] != target
                //based on current information, we can only move left pointer to skip one cell
                //thus in the worest case, we would have target: 2, and array like 11111111, then
                //the running time would be O(n)
                start++;
            }
        }
        return false;
    }
```
