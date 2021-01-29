---
title: "179. Largest Number"
date: "2016-07-21 01:07:28"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
179- Largest Number
 **Question
Editorial Solution

 [My Submissions](https://leetcode.com/problems/largest-number/submissions/)

Total Accepted: **50334**
Total Submissions: **253493**
Difficulty: **Medium**

Given a list of non negative integers, arrange them such that they form the largest number.
For example, given [3, 30, 34, 5, 9]
, the largest formed number is 9534330
.
Note: The result may be very large, so you need to return a string instead of an integer.
**Credits:**Special thanks to [@ts](https://oj.leetcode.com/discuss/user/ts) for adding this problem and creating all test cases.

Hide Tags
 [Sort](https://leetcode.com/tag/sort/)

```java
  /*The idea here is basically implement a String comparator to decide which String should come first during concatenation. Because when you have 2 numbers (let's convert them into String), you'll face only 2 cases:
        For example:
        
        String s1 = "9";
        String s2 = "31";
        
        String case1 =  s1 + s2; // 931
        String case2 = s2 + s1; // 319
        
        Apparently, case1 is greater than case2 in terms of value.
        So, we should always put s1 in front of s2.
        https://discuss.leetcode.com/topic/8018/my-java-solution-to-share
    */
    public String largestNumberJava7(int[] nums) {
        if (nums == null || nums.length == 0) return null;
        String[] strArr = new String[nums.length];
        for (int i = 0; i < nums.length; i++) {
            strArr[i] = String.valueOf(nums[i]);
        }
        // Comparator to decide which string should come first in concatenation
        Comparator<String> comp = new Comparator<String>(){
             @Override 
             public int compare(String str1, String str2) {
                 String s1 = str1 + str2;
                 String s2 = str2 + str1;
                 return s2.compareTo(s1); // reverse order here, so we can do append() later
             }
        };
        
        Arrays.sort(strArr, comp);
        
        // An extreme edge case by lc, say you have only a bunch of 0 in your int array
        if(strArr[0].charAt(0) == '0')
           return "0";
            
        
        StringBuilder sb = new StringBuilder();
        for (String str : strArr) {
            sb.append(str);
        }
        
        return sb.toString();
    }
    
    // https://discuss.leetcode.com/topic/7235/my-3-lines-code-in-java-and-python
    public String largestNumber(int[] num) {  // Thanks for Java 8, it makes code beautiful.
        String[] array = Arrays.stream(num).mapToObj(String::valueOf).toArray(String[]::new);
        Arrays.sort(array, (String s1, String s2) -> (s2 + s1).compareTo(s1 + s2));
        return Arrays.stream(array).reduce((x, y) -> x.equals("0") ? y : x + y).get();
    }
```
