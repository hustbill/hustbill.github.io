---
title: "244. Shortest Word Distance II"
date: "2016-12-24 12:25:00"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
 [My Submissions](https://leetcode.com/problems/shortest-word-distance-ii/submissions/)

Total Accepted: **16006**
Total Submissions: **46068**
Difficulty: **Medium**
Contributors: **Admin**

This is a **follow up** of [Shortest Word Distance](https://leetcode.com/problems/shortest-word-distance). The only difference is now you are given the list of words and your method will be called *repeatedly* many times with different parameters. How would you optimize it?
Design a class which receives a list of words in the constructor, and implements a method that takes two words *word1* and *word2* and return the shortest distance between these two words in the list.
For example,Assume that words = ["practice", "makes", "perfect", "coding", "makes"]
.
Given *word1* = “coding”
, *word2* = “practice”
, return 3.Given *word1* = "makes"
, *word2* = "coding"
, return 1.
**Note:**You may assume that *word1* **does not equal to** *word2*, and *word1* and *word2* are both in the list.

Hide Company Tags
 [LinkedIn](https://leetcode.com/company/linkedin/)
Hide Tags
 [Hash Table](https://leetcode.com/tag/hash-table/) [Design](https://leetcode.com/tag/design/)
Hide Similar Problems
 [(E) Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/) [(E) Shortest Word Distance](https://leetcode.com/problems/shortest-word-distance/) [(M) Shortest Word Distance III](https://leetcode.com/problems/shortest-word-distance-iii/)
```java
public class WordDistance {

    Map<String, List<Integer>> map;
    
    public WordDistance(String[] words) {
         map = new HashMap<>();
         for (int i = 0; i < words.length; i++) {
             List<Integer> list;
             if (map.containsKey(words[i])) {
                 list =  map.get(words[i]);
                 list.add(i);
             } else {
                 list = new ArrayList<>();
                 list.add(i);
             }
              map.put(words[i], list);
         }
    }

    public int shortest(String word1, String word2) {
        List<Integer> l1 = map.get(word1);
        List<Integer> l2 = map.get(word2);
        
        int min = Integer.MAX_VALUE;
        for (int p1 : l1) {
            for (int p2 : l2) {
                min = Math.min(min, Math.abs(p2 - p1));
            }
        }
        return min;
    }
}

// Your WordDistance object will be instantiated and called as such:
// WordDistance wordDistance = new WordDistance(words);
// wordDistance.shortest("word1", "word2");
// wordDistance.shortest("anotherWord1", "anotherWord2");
```
