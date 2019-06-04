# Jewels and Stones
You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".

Example 1:  
Input: J = "aA", S = "aAAbbbb"  
Output: 3

Example 2:  
Input: J = "z", S = "ZZ"  
Output: 0
Note:

S and J will consist of letters and have length at most 50.  
The characters in J are distinct.

字符串J中每个字母都代表宝石，字符串S代表你拥有的所有石头，找出你有多少块宝石。  
注意：J中每个字母都是不同的，且大小写分别代表不同的石头

-----

## 解法一
取出J中每个字母，遍历字符串S求得每个字母的个数并求和, 中间可以消去已确定字母

### javascript版
```

var numJewelsInStones = function(J, S) {
    var sum = 0;
    for(var letter of J) {
        var temp = S.replace(new RegExp(letter, 'g'), '');
        sum += (S.length - temp.length);
        S = temp;
    }
    return sum;
};

```

- 时间： 52ms
- 内存： 34MB

