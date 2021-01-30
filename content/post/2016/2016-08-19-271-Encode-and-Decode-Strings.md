---
title: "271. Encode and Decode Strings"
date: "2016-08-19 16:00:03"
draft: false
categories: [LeetCode]
hiddenFromHomePage: true
---
271- Encode and Decode Strings
 **Question
Editorial Solution

 [My Submissions](https://leetcode.com/problems/encode-and-decode-strings/submissions/)

Total Accepted: **9668**
Total Submissions: **35396**
Difficulty: **Medium**

Design an algorithm to encode **a list of strings** to **a string**. The encoded string is then sent over the network and is decoded back to the original list of strings.
Machine 1 (sender) has the function:
string encode(vector<string> strs) { // ... your code return encoded_string;}
Machine 2 (receiver) has the function:vector<string> decode(string s) { //... your code return strs;}

So Machine 1 does:
string encoded_string = encode(strs);

and Machine 2 does:
vector<string> strs2 = decode(encoded_string);

strs2
 in Machine 2 should be the same as strs
 in Machine 1.
Implement the encode
 and decode
 methods.
**Note:**
The string may contain any possible characters out of 256 valid ascii characters. Your algorithm should be generalized enough to work on any possible characters.
Do not use class member/global/static variables to store states. Your encode and decode algorithms should be stateless.
Do not rely on any library method such as eval
 or serialize methods. You should implement your own encode/decode algorithm.

Hide Company Tags
 [Google](https://leetcode.com/company/google/)
Hide Tags
 [String](https://leetcode.com/tag/string/)
Hide Similar Problems
 [(E) Count and Say](https://leetcode.com/problems/count-and-say/) [(H) Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/)
```java
public class Codec {

    // https://discuss.leetcode.com/topic/22848/ac-java-solution 
    // Encodes a list of strings to a single string.
    public String encode(List<String> strs) {
        StringBuilder sb = new StringBuilder();
        for (String s : strs) {
            sb.append(s.length()).append('/').append(s);
        }
        return sb.toString();
    }

    // Decodes a single string to a list of strings.
    public List<String> decode(String s) {
        List<String> ret = new ArrayList<String>();
        int i = 0;
        while (i < s.length()) {
            int slash = s.indexOf('/', i);
            int size = Integer.valueOf(s.substring(i, slash));
            ret.add(s.substring(slash + 1, slash + size + 1));
            i = slash + size + 1;
        }
        return ret;
    }
}

// Your Codec object will be instantiated and called as such:
// Codec codec = new Codec();
// codec.decode(codec.encode(strs));
```
