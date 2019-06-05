# Median of Two Sorted Arrays

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume nums1 and nums2 cannot be both empty.

Example 1:
```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```


Example 2:
```
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
```

找出两个有序数组的中位数

-----

## 解法一
每次去除最大最小两个数字 最后会剩一个或两个数字，再求解  
**时间复杂度不符合要求**
### javascript 版
```
var findMedianSortedArrays = function(nums1, nums2) {
    while(true) {
        if (nums1.length === 0) {
            return findMedianSortedArray(nums2);
        } else if(nums2.length === 0) {
            return findMedianSortedArray(nums1);
        } else if(nums1.length === 1 && nums2.length === 1){
            return (nums1[0] + nums2[0]) / 2;
        } else {
            if (nums1[nums1.length - 1] > nums2[nums2.length - 1]) {
                nums1.pop();
            } else {
                nums2.pop();
            }
            if (nums1[0] < nums2[0] || nums2.length === 0) {
                nums1.shift();
            } else {
                nums2.shift();
            }
        }
    }
};

var findMedianSortedArray = function(nums) {
    if (nums.length % 2 === 1) {
        return nums[(nums.length - 1) / 2];
    } else {
        return (nums[nums.length/ 2] + nums[nums.length/ 2 - 1]) / 2;
    }
}
```
时间|内存|时间复杂度|空间复杂度
:--:|:--:|:--:|:--:
116ms|38.6MB|O(n)|O(n)


