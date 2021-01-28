---
title: "228. Summary Ranges  "
date: "2016-09-22 15:32:59"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
228 Summary Ranges  
Difficulty: Medium
Given a sorted integer array without duplicates, return the summary of its ranges.
For example, given [0,1,2,4,5,7], return ["0->2","4->5","7"].
```java
 public List<String> summaryRanges(int[] nums) {
        // Ref : https://leetcode.com/discuss/42290/accepted-java-solution-easy-to-understand
        List<String> list = new ArrayList<String>();
        
       for (int i=0; i < nums.length; i++) {
           int num = nums[i];
           while (i +1 < nums.length && (nums[i+1] - nums[i]) == 1) {
             i++;
           }
           if (num != nums[i]) {
               list.add(num + "->" + nums[i]);
           } else {
               list.add(num + "");
           }
       }
       return list;
    }
}
```
