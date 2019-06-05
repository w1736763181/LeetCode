# Longest Palindromic Substring

Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

Example 1:
```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```


Example 2:
```
Input: "cbbd"
Output: "bb"
```

找出最长的回文子字符串

-----

## 解法一
每次去除最大最小两个数字 最后会剩一个或两个数字，再求解  
**时间复杂度不符合要求**
### javascript 版
```
var longestPalindrome = function(s) {
    var str = '';
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
    return str;
};
```
时间|内存|时间复杂度|空间复杂度
:--:|:--:|:--:|:--:
116ms|38.6MB|O(n)|O(n)


