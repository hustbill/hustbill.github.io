---
title: "345. Reverse Vowels of a String"
date: "2017-06-16 15:17:31"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Write a function that takes a string as input and reverse only the vowels of a string.

Example 1:
Given s = "hello", return "holle".

Example 2:
Given s = "leetcode", return "leotcede".

Note:
The vowels does not include the letter "y".

**解题思路 **  
Two pointers. Use a HashSet<Character> to reduce the look up time to O(1)  

```java
    public String reverseVowels(String s) {
        Set<Character> vowels = new HashSet<>(Arrays.asList(new Character[]{'a','e','i','o','u','A','E','I','O','U'}));
        
        char[] list = s.toCharArray();
        for (int i=0, j=list.length-1; i<j; ) {
            if (!vowels.contains(list[i])) {
                i++;
                continue;
            }
            if (!vowels.contains(list[j])) {
                j--;
                continue;
            }
            char temp=list[i];
            list[i]=list[j];
            list[j]=temp;
            i++;
            j--;
        }
       return String.valueOf(list);
    }

public String reverseVowels(String s) {
    if(s == null || s.length()==0) return s;
    String vowels = "aeiouAEIOU";
    char[] chars = s.toCharArray();
    int start = 0;
    int end = s.length()-1;
    while(start<end){
        
        while(start<end && !vowels.contains(chars[start]+"")){
            start++;
        }
        
        while(start<end && !vowels.contains(chars[end]+"")){
            end--;
        }
        
        char temp = chars[start];
        chars[start] = chars[end];
        chars[end] = temp;
        
        start++;
        end--;
    }
    return new String(chars);
}
```
