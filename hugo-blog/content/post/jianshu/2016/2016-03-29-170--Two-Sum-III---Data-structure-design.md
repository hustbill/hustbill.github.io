---
title: "170. Two Sum III - Data structure design"
date: "2016-03-29 08:47:37"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---

```java
/*
Date: March 21, 2016
170. Two Sum III - Data structure design
[My Submissions](https://leetcode.com/problems/two-sum-iii-data-structure-design/submissions/)Question

Total Accepted: **10075** Total Submissions: **41802** Difficulty: **Easy**

Design and implement a TwoSum class. It should support the following operations: add
 and find
.
add
 - Add the number to an internal data structure.find
 - Find if there exists any pair of numbers which sum is equal to the value.
For example,
add(1); add(3); add(5);find(4) -> truefind(7) -> false

Hide Company Tags
 [LinkedIn](https://leetcode.com/company/linkedin/)
Hide Tags
 [Hash Table](https://leetcode.com/tag/hash-table/) [Design](https://leetcode.com/tag/design/)
Hide Similar Problems
 [(E) Two Sum](https://leetcode.com/problems/two-sum/) [(E) Unique Word Abbreviation](https://leetcode.com/problems/unique-word-abbreviation/)
*/

import java.util.*;

public class TwoSumDataStructure {
	// add  O(1) time,    find(value) O(n) time,  space O(n)
	public static void main(String args[]) {
		TwoSumDataStructure twoSum = new TwoSumDataStructure();
		twoSum.add(1); twoSum.add(3); twoSum.add(5);
		System.out.printf(" find(4) = %b\n", twoSum.find(4));
		System.out.printf(" find(7) = %b\n", twoSum.find(7));
	}
	
	private static HashMap<Integer, Integer> map = new HashMap<>();

	public static void add(int input) {
		int count = map.containsKey(input) ? map.get(input) : 0;
		map.put(input, count + 1);
	}


	public static boolean find(int val) {
		for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
			int num = entry.getKey();
			int y = val - num;
			if (y == num) {
				// For dumplicates, ensure there are at least  two individual numbers.
				if (entry.getValue() >= 2)  return true;
			} else if (map.containsKey(y)) {
				return true;
			}
		}
		return false;
	} 

}
```
