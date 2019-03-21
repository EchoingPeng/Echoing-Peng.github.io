---
layout: single
title:  "Longest Substring Without Repeating Characters"
date:   2019-01-15 
description: Leetcode solution 
---
Given a string, you need to find the length of the longest substring without repeating characters.

```
Example 1:

Input: "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.

Example 2:

Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Example 3:

Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```


Solution: 

```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if(s == null || s.length() == 0) return 0;
        char[] arr = s.toCharArray();
        int max = Integer.MIN_VALUE;
        for(int i = 0; i < arr.length; i++) {
            Set<Char> set = new HashSet<>();
            
            for(int j = i; j < arr.length; j++) {
                if(!set.contains(arr[j]))
                    set.add(arr[j]);
                    
                else { 
                    max = Math.max(max, set.size());
                    break;
                }
            }
            max = Math.max(set.size(), max);
        }
        return max;
    }
}
```

