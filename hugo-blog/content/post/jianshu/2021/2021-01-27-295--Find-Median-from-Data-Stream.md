---
title: "295--Find-Median-from-Data-Stream"
date: "2017-04-26"
draft: false
categories: [user-1647554-1611798760]
hiddenFromHomePage: true
---
 [My Submissions](https://leetcode.com/problems/find-median-from-data-stream/submissions/)

Difficulty: **Hard**

Median is the middle value in an ordered integer list. If the size of the list is even, there is no middle value. So the median is the mean of the two middle value.
Examples: [2,3,4]
 , the median is 3

[2,3]
, the median is (2 + 3) / 2 = 2.5

Design a data structure that supports the following two operations:
void addNum(int num) - Add a integer number from the data stream to the data structure.
double findMedian() - Return the median of all elements so far.

For example:
add(1)add(2)findMedian() -> 1.5add(3) findMedian() -> 2
**Credits:**Special thanks to [@Louis1992](https://leetcode.com/discuss/user/Louis1992) for adding this problem and creating all test cases.

Hide Company Tags
 [Google](https://leetcode.com/company/google/)
Hide Tags
 [Heap](https://leetcode.com/tag/heap/) [Design](https://leetcode.com/tag/design/)
```java
import java.util.*;

public class MedianFinder {

	PriorityQueue<Integer> minHeap = new PriorityQueue(); // heap is a minimal heap by default
	PriorityQueue<Integer> maxHeap = new PriorityQueue(Collections.reverseOrder()); // change to a maximum heap
	
	/* 演算过程
		maxHeap    minHeap
		2			
					2
		2
		3, 2		
		2			3
		4, 2		3
		2			3,4
		2, 3		4
		====================>  return maxHeap.peek()  =3 
		*/
	
    // Adds a number into the data structure.
    public void addNum(int num) {
        maxHeap.offer(num);
		minHeap.offer(maxHeap.poll());
		if (maxHeap.size() < minHeap.size()) {
			maxHeap.offer(minHeap.poll());
		}
    }

    // Returns the median of current data stream
    public double findMedian() {
        if (minHeap.size() == maxHeap.size()) {
        	return  (maxHeap.peek() + minHeap.peek()) / 2.0;
        } else {
        	return maxHeap.peek();
        }
    }
	
	public static void main(String[] args) {
		MedianFinder mf = new MedianFinder();
		mf.addNum(2);
		mf.addNum(3);
		mf.addNum(4);
		System.out.println(mf.findMedian());
	}
}

// Your MedianFinder object will be instantiated and called as such:
// MedianFinder mf = new MedianFinder();
// mf.addNum(1);
// mf.findMedian();
```
