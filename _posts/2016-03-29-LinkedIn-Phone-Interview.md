---
layout: post
title: "LinkedIn Phone Interview Questions"
date: 2016-03-29 13:33:00
categories: jekyll update
---

``java

// Given a sorted array that has been transposed (that is, a portion has been removed from one end and attached to the other), write a function to determine if a given number is present in the array.
// For example, here's a transposed array: 6 7 1 2 3 4 5. Note: numbers don't have to be sequential.
// Task #1: Find number "1". Should return true (or index "2").
// Task #2: Find number "4". Should return true (or index "5").

// 1. Find the tranposed pos. return index 2
// 2. do binary search to check the target

<!-- begin     mid     end
6     7 1  2  3 4  5

6 7 1 2 3 4 5
Search for 7

1 1 2 1 1 1 1 1 1 1 -->

public class solution {
    public boolean findTarget (int[] array, int target) {
        if (array == null || array.length == 0) return false;
        
        int n = array.length;
        int begin = 0;
        int end = n -1;
        
        while (begin <= end) {
           int mid = begin + (end - begin) /2;
            int midVal = array[mid];
            if (midVal == target) return true;
            
            if (array[begin] <= midVal) {   
                if ( target < midVal && target >= array[begin]){
                    end = mid - 1;
                } else { 
                     begin = mid + 1;
                }
            }
            if (  midVal <= array[end]) {
                if (target > midVal && target <= array[end]) {
                    begin = mid + 1;
                 else {
                     end = mid -1;
                 }
            }
        }
        
        return false;
    }
}


/* This class will be given a list of words (such as might be tokenized
 * from a paragraph of text), and will provide a method that takes two
 * words and returns the shortest distance (in words) between those two
 * words in the provided text.
 * Example:
 *   WordDistanceFinder finder = new WordDistanceFinder(Arrays.asList("the", "quick", "brown", "fox", "quick"));
 *   assert(finder.distance("fox","the") == 3);
 *   assert(finder.distance("quick", "fox") == 1);
 *
 * "quick" appears twice in the input. There are two possible distance values for "quick" and "fox":
 *     (3 - 1) = 2 and (4 - 3) = 1.
 * Since we have to return the shortest distance between the two words we return 1.
 */
public class WordDistanceFinder {
    public String[] wordArr;
    
    public WordDistanceFinder (List<String> words) {
        // implementation here
       // HashMap<, Integer> map = new HashMap<>(); doesn't work
        
        HashMap<String, List<Integer>>  map = new HashMap<>();
       // list of words
      
       
    }
    public int distance (String wordOne, String wordTwo) {
        // implementation here
         int i1 = -1, i2 = -1;
         int min =  words.length;
         for (int i = 0; i < words.length; i++) {
             String word = words[i];
             if (word.equals(wordOne) ) {
                 i1= i;
                 if ( i2 >= 0) min = Math.min(min, i1 - i2);
             } else if (word.equals(wordTwo)) {
                 i2 = i;
                 if ( i1 >= 0) min = Math.min(min, i2- i1);
             }
         }
         return min;
    }
}

