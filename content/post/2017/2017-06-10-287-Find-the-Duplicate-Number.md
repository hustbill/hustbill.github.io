---
title: "287. Find the Duplicate Number"
date: "2017-06-10 09:42:01"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
[**Description](https://leetcode.com/problems/find-the-duplicate-number/#/description)[**Hints](https://leetcode.com/problems/find-the-duplicate-number/#/hints)[**Submissions](https://leetcode.com/problems/find-the-duplicate-number/#/submissions)[**Solutions](https://leetcode.com/problems/find-the-duplicate-number/#/solutions)

Total Accepted: **67370**
Total Submissions: **157182**
Difficulty: **Medium**
Contributor: **LeetCode**

Given an array *nums* containing *n* + 1 integers where each integer is between 1 and *n* (inclusive), prove that at least one duplicate number must exist. Assume that there is only one duplicate number, find the duplicate one.
**Note:**
You **must not** modify the array (assume the array is read only).
You must use only constant, *O*(1) extra space.
Your runtime complexity should be less than O(n2
)
.
There is only one duplicate number in the array, but it could be repeated more than once.

**Credits:**Special thanks to [@jianchao.li.fighter](https://leetcode.com/discuss/user/jianchao.li.fighter) for adding this problem and creating all test cases.

Hide Company Tags
 [Bloomberg](https://leetcode.com/company/bloomberg/)
Hide Tags
 [Binary Search](https://leetcode.com/tag/binary-search/) [Array](https://leetcode.com/tag/array/) [Two Pointers](https://leetcode.com/tag/two-pointers/)
Hide Similar Problems
 [(H) First Missing Positive](https://leetcode.com/problems/first-missing-positive/) [(E) Single Number](https://leetcode.com/problems/single-number/) [(M) Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/) [(E) Missing Number](https://leetcode.com/problems/missing-number/)

** 解题思路 **
两种解法：   
- Two pointer 
- Binary search   


## Two Pointer   ##
Use Two pointers,  O(n) Time , O(1) space, without changing the input array  
      The main idea is the same with problem Linked List CycleII, https://leetcode.com/problems/linked-list-cycle-ii/. 
        Use two pointers the fast and the slow. The fast one goes forward two steps each time, while the slow one goes only step each time. They must meet the same item when slow==fast. In fact, they meet in a circle, the duplicate number must be the entry point of the circle when visiting the array from nums[0]. 
        Next we just need to find the entry point. We use a point(we can use the fast one before) to visit form begining with one step each time, do the same job to slow. When fast==slow, they meet at the entry point of the circle. The easy understood code is as follows.

## Binary Search 
Binary Search,  O(nlog(n)) , O(1) space, without changing the input array   
     Let count be the number of elements in the range 1 .. mid,    
    -If count > mid, then there are more than mid elements in the range 1 .. mid and thus that range contains a duplicate.  
     If count <= mid, then there are n+1-count elements in the range mid+1 .. n. That is, at least n+1-mid elements in a range of size n-mid. Thus this range must 
contain a duplicate.  
**鸽巢原理**，又名**[狄利克雷](https://zh.wikipedia.org/wiki/%E7%B4%84%E7%BF%B0%C2%B7%E5%BD%BC%E5%BE%97%C2%B7%E7%8B%84%E5%88%A9%E5%85%8B%E9%9B%B7)抽屉原理**、**鸽笼原理**。
其中一种简单的表述法为：
若有n个笼子和n+1只鸽子，所有的鸽子都被关在鸽笼里，那么至少有一个笼子有至少2只鸽子。
另一种为：
若有n个笼子和kn+1只鸽子，所有的鸽子都被关在鸽笼里，那么至少有一个笼子有至少k+1只鸽子。
```java
/*   Solution 1:  Two pointers,  O(n) Time , O(1) space, without changing the input array 
      The main idea is the same with problem Linked List Cycle II,https://leetcode.com/problems/linked-list-cycle-ii/. 
        Use two pointers the fast and the slow. The fast one goes forward two steps each time, while the slow one goes only step each time. They must meet the same item when slow==fast. In fact, they meet in a circle, the duplicate number must be the entry point of the circle when visiting the array from nums[0]. 
        Next we just need to find the entry point. We use a point(we can use the fast one before) to visit form begining with one step each time, do the same job to slow. When fast==slow, they meet at the entry point of the circle. The easy understood code is as follows.
    */
    public int findDuplicate(int[] nums) {
      if (nums.length > 1) {
          int slow = nums[0];
          int fast = nums[nums[0]];
          while (slow != fast) {
              slow = nums[slow];
              fast = nums[nums[fast]];
          }
          fast = 0;
          while (fast != slow) {
              fast = nums[fast];
              slow = nums[slow];
          }
          return slow;
      }
      return -1;
        
    }
  
    
    /*
     Solution 2:  Binary Search,  O(nlog(n)) , O(1) space, without changing the input array 
     Let count be the number of elements in the range 1 .. mid,
     If count > mid, then there are more than mid elements in the range 1 .. mid and thus that range contains a duplicate.
     If count <= mid, then there are n+1-count elements in the range mid+1 .. n. That is, at least n+1-mid elements in a range of size n-mid. Thus this range must contain a duplicate.
    */
    public int findDuplicateBinarySearch(int[] nums) {
      int start = 0, end = nums.length - 1;
      while (start <= end) {
          int mid = start + (end - start) / 2;
          int count = 0;
          for (int i : nums) {
              if (i <= mid) {
                  count++;
              }
          }
          if (count <= mid){
              start = mid + 1;
          } else {
              end = mid - 1;
          }
      }
      return start;
    }
    
    // find the only one duplicate, occur once
    public int findOnlyOneDuplicate(int[] nums) {
      // sum (nums[0] , nums[n]) 
      int sum = 0;
      int secondSum = 0;
      
      for (int i = 0; i < nums.length; i++) {
          sum += nums[i];
      }
      
      secondSum = (1 + nums.length - 1) * (nums.length - 1) / 2;
      return sum - secondSum;
    }
```
