---
title: "34. Search for a Range"
date: "2016-07-26 01:01:31"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Total Accepted: **91870**
Total Submissions: **308813**
Difficulty: **Medium**

Given a sorted array of integers, find the starting and ending position of a given target value.
Your algorithm's runtime complexity must be in the order of *O*(log *n*).
If the target is not found in the array, return [-1, -1]
.
For example,Given [5, 7, 7, 8, 8, 10]
 and target value 8,return [3, 4]
.

Hide Company Tags
 [LinkedIn](https://leetcode.com/company/linkedin/)
Hide Tags
 [Binary Search](https://leetcode.com/tag/binary-search/) [Array](https://leetcode.com/tag/array/)
Hide Similar Problems
 [(E) First Bad Version](https://leetcode.com/problems/first-bad-version/)
```java
   // https://discuss.leetcode.com/topic/6327/a-very-simple-java-solution-with-only-one-binary-search-algorithm
    public int[] searchRange(int[] A, int target) {
		int start = firstGreaterEqual(A, target);
		if (start == A.length || A[start] != target) {
			return new int[]{-1, -1};
		}
		int second = firstGreaterEqual(A, target + 1) - 1;
		return new int[]{start, second};
	}

	//find the first number that is greater than or equal to target.
	//could return A.length if target is greater than A[A.length-1].
	//actually this is the same as lower_bound in C++ STL.
	private int firstGreaterEqual(int[] A, int target) {
		int low = 0, high = A.length;
		while (low < high) {
			int mid = low + ((high - low) >> 1);
			//low <= mid < high
			if (A[mid] < target) {
				low = mid + 1;
			} else {
				//should not be mid-1 when A[mid]==target.
				//could be mid even if A[mid]>target because mid<high.
				high = mid;
			}
		}
		return low;
	}
```
