# Add Two Numbers
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example:  
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```

每个数字用反序链表保存， 如 "5 -> 0 -> 1" 代表 105   
对两个列表中的数字求和并用相同的方式输出

-----

## 解法一

解析每个链表获得数字，对两个数字相加，并将结果转换成链表形式。  

**链表太长，数字太大会出现错误。**

### javascript 版

```
var addTwoNumbers = function(l1, l2) {
    return list2Num(l1) + list2Num(l2);
};

var list2Num = function(l) {
    var i = 0;
    var ret = 0;
    while(l !== null) {
        ret += l.val * Math.pow(10, i);
        i++;
        l = l.next;
    }
    return ret;
}

var num2List = function(num) {
    if (num === 0) {
        return {
            val: 0
        };
    }
    if (num < 0) {
        throw new Exception('wrong number');
    }
    var ret = {};
    var cur = ret;
    while(true) {
        cur.val = num % 10;
        num = Math.floor(num / 10);
        if (num === 0) {
            return ret;
        }
        cur.next = {};
        cur = cur.next;
    }
    return;
}

```


## 解法二

链表相加，过10进1

### javascript 版

```
var addTwoNumbers = function(l1, l2) {
    var cur = {
        val: 0
    };
    var ret = cur;
    var n1;
    var n2;
    while(true) {
        n1 = (l1 && l1.val) || 0
        n2 = (l2 && l2.val) || 0
        var sum = n1 + n2 + cur.val;
        cur.val = sum % 10;
        l1 = l1 && l1.next;
        l2 = l2 && l2.next;
        var n = Math.floor(sum / 10);
        if ((l1 || l2) || n > 0) {
            cur.next = {
                val: n
            };
            cur = cur.next;
        } else {
            return ret;
        }
    }
};

```

时间|内存|时间复杂度|空间复杂度
:--:|:--:|:--:|:--:
116ms|39.6MB|O(n)|O(n)
