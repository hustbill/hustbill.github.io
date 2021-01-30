---
title: "17. Letter Combinations of a Phone Number"
date: "2017-06-24 12:39:47"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
Given a digit string, return all possible letter combinations that the number could represent.
A mapping of digit to letters (just like on the telephone buttons) is given below.
![](http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)
**Input:**Digit string "23"**Output:** ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].

**解题思路 ** 
两种解法： 1. back tracking  2. iterative 用一个Queue存取中间结果。  

```java

 // back tracking
    private static final String[] KEYS = {"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz" };
    public List<String> letterCombinations(String digits) {
      if (digits == null || digits.length() == 0)  return new ArrayList<String>();
      List<String> ret = new LinkedList<String>();
      backtrack("", digits, 0, ret);
      return ret;
    }
    
    private void backtrack(String prefix, String digits, int offset, List<String> ret) {
        if (offset >= digits.length()) {
            ret.add(prefix);
            return;
        }
        String letters = KEYS[(digits.charAt(offset) - '0')];
        for (int i = 0; i < letters.length(); i++) {
            backtrack(prefix + letters.charAt(i), digits, offset + 1, ret);
        }
    }
    
    /*
      Iterative solution. For each digit added, remove and copy every element in the queue and add the possible letter to each element, then add the updated elements back into queue again. Repeat this procedure until all the digits are iterated.
    */
    public List<String> letterCombinationsItr(String digits) {
      List<String> list = new ArrayList<>();
      if (digits == null || digits.length() == 0) return list;
      
      LinkedList<String> res = new LinkedList<String>();  // use a queue 
      
      String[] mapping = new String[] { "0", "1", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
      
      res.add("");
      for (int i = 0; i < digits.length(); i++) {
          int x = Character.getNumericValue(digits.charAt(i));
          while (res.peek().length() == i) {
              String t = res.remove();
              for (char s : mapping[x].toCharArray()) {
                  res.add(t + s);
              }
          }
      }
      return res;
    }
```
