---
title: "378. Find the kth smallest number in at row and column sorted matrix"
date: "2017-05-07 13:46:21"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
```code
/*
 *  378. Find the kth smallest number in at row and column sorted matrix.
 */
public class KthSmallest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		int[][] matrix = {
		                  {1 ,5 ,7},
		                  {3 ,7 ,8},
		                  {4 ,8 ,9},
					};
		KthSmallest ks = new KthSmallest();
		
		int k = 4;
		int res = ks.kthSmallest(matrix, k);
		System.out.println("res: " + res);
	}
	
	/*
	 *  解题报告：
             Java 1ms nlog(max -min) solution
		Main loop is binary search of max - min.
		Swap from left-bottom to right-top can get count <= mid in O(n) time instead of O(nlogn), 

		total complexity will be O(nlogm) while m = max - min.
		ref: https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/#/solutions
	 */
	public int kthSmallest(int[][] matrix, int k) {
		int n = matrix.length;
		int lo = matrix[0][0], hi = matrix[n-1][n-1];
		while (lo <= hi) {
			int mid = lo + (hi - lo) / 2;
			int cout = getLessEqual(matrix, mid);
			
			if (cout < k) lo = mid + 1;
			else 
				hi = mid - 1;
		}
		return lo;
			
	}
	
	public int getLessEqual(int[][] matrix, int val) {
		int res = 0;
		int n = matrix.length;
		int i = n - 1, j = 0;
        while (i >= 0 && j < n) {
        	if (matrix[i][j] > val) i--;
        	else {
        		res += i + 1;
        		j++;
        	}
        }
        return res;
	}
}
```
