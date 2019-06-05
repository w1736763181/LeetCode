# Longest Substring Without Repeating Characters

Given a string, find the length of the longest substring without repeating characters.  

Example 1:
```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```


Example 2:
```
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

Example 3:
```
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

找一个字符串中含有不同字母最多的子串，返回其长度

-----

## 解法一
遍历两次数组，找到每个下标开始的最长不同字母子串长度
### javascript 版
```
var lengthOfLongestSubstring = function(s) {
    var max = 0;
    var set = new Set();
    for(var i = 0; i < s.length; i++) {
        for (var j = i; j < s.length; j++) {
            if (set.has(s.charAt(j))) {
                max = Math.max(max, j - i);
                set.clear();
                break;
            } else if(j === s.length - 1) {
                max = Math.max(max, j - i + 1);
            } else {
                set.add(s.charAt(j));
            }
        }
    }
    return max;
};
```
时间|内存|时间复杂度|空间复杂度
:--:|:--:|:--:|:--:
288ms|41MB|O(n²)|O(n)

## 解法二
用map来优化解法一效率
### javascript 版
```
var lengthOfLongestSubstring = function(s) {
    var max = 0;
    var map = new Map();
    var startIndex = 0;
    for(var i = 0; i < s.length; i++) {
        var char = s.charAt(i);
        if (map.has(char) && map.get(char) >= startIndex) {
            max = Math.max(i - startIndex, max);
            startIndex = map.get(char) + 1;
        } else if (i === s.length - 1) {
            max = Math.max(i - startIndex + 1, max);
        }
        map.set(char, i);
    }
    return max;
};
```
时间|内存|时间复杂度|空间复杂度
:--:|:--:|:--:|:--:
76ms|37.4MB|O(n)|O(n)

