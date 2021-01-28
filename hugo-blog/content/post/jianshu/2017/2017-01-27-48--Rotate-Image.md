---
title: "48. Rotate Image"
date: "2017-01-27 16:07:41"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
You are given an n x n 2D matrix representing an image.  

Rotate the image by 90 degrees (clockwise).  

Follow up:  
Could you do this in-place?  
5/17/19 店面
```java
/*
The idea was firstly transpose the matrix and then flip it symmetrically.
For instance,

1  2  3             
4  5  6
7  8  9
after transpose, it will be swap(matrix[i][j], matrix[j][i])
转置矩阵
1  4  7
2  5  8
3  6  9
Then flip the matrix horizontally. （水平翻转）
(swap(matrix[i][j], matrix[i][matrix.length-1-j])

7  4  1
8  5  2
9  6  3
 */
    public void rotate(int[][] matrix) {
        for (int i = 0; i < matrix.length; i++) {
            for (int j = i; j < matrix[0].length; j++) {
                int temp = 0;
                temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        
        
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix.length/2 ;j++) {
                int temp = 0;
                temp = matrix[i][j];
                matrix[i][j] = matrix[i][matrix.length -1 -j];
                matrix[i][matrix.length - 1 -j] = temp;
            }
        }
        
    }
```

## 第二种思路
```java
    /*
 * clockwise rotate
 * first reverse up to down, then swap the symmetry 
 * 1 2 3     7 8 9     7 4 1
 * 4 5 6  => 4 5 6  => 8 5 2
 * 7 8 9     1 2 3     9 6 3
*/


/*
 * anticlockwise rotate
 * first reverse left to right, then swap the symmetry
 * 1 2 3     3 2 1     3 6 9
 * 4 5 6  => 6 5 4  => 2 5 8
 * 7 8 9     9 8 7     1 4 7
*/
// Ref: https://leetcode.com/discuss/20589/a-common-method-to-rotate-the-image
    // test case: [[1,2,3], [4,5,6],[7,8,9]]
    public void rotate(int[][] matrix) {
        if(matrix.length <=1) return;
        int m = matrix.length, n = matrix[0].length;
        swapRows(matrix);
            
        // [[1,2,3,4],[5,6,7,8],[9,10,11,12],[13,14,15,16]]    
        for (int i=0; i < m; ++i) {
            for (int j= i+1; j< n; ++j) {
                  int temp = matrix[i][j];
                  matrix[i][j] = matrix[j][i];
                  matrix[j][i] = temp;
            }
        }
    }
    
    public void  swapRows(int[][]  A) {
        // swap rows
        int len = A.length;
        for (int i=0; i< len/2; i++) {
           int[] tmp = A[i];
            A[i] = A[len-1-i];
            A[len-1-i] = tmp;
        }
    }
```
