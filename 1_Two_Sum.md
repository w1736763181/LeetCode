# Two Sum
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:  
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

取出一个数组内相加正好等于某一值的两个元素的数组下标。  
注意： 只有一个解，而且一个元素不能使用两次。

-----

## 解法一

遍历两边数组，相加看是否为目标值，返回结果 

### javascript 版

```
var twoSum = function(nums, target) {
    for(var i = 0; i < nums.length - 1; i++) {
        for(var j = i + 1; j < nums.length; j++) {
            if (nums[i] + nums[j] === target) {
                return [i, j];
            }
        }
    }
};

```

时间|内存|时间复杂度|空间复杂度
:--:|:--:|:--:|:--:
104ms|34.7MB|O(n²)|O(1)


## 解法二

可以使用map的来优化解法一的效率

### javascript 版

```
var twoSum = function(nums, target) {
    var map = new Map();
    for(var index in nums) {
        var n = nums[index];
        var i = map.get(target - n);
        if (i !== undefined) {
            return [i, index];
        }

        map.set(n, index);
    }
};

```

时间|内存|时间复杂度|空间复杂度
:--:|:--:|:--:|:--:
56ms|35.8MB|O(n)|O(n)
