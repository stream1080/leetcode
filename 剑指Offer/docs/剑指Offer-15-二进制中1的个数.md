# 剑指Offer-15-二进制中1的个数

## [题目链接](https://leetcode-cn.com/problems/er-jin-zhi-zhong-1de-ge-shu-lcof/)


## 解析

- 把一个整数减去1，再和原整数做与运算，会把该整数最右边一个1变成0.
- 那么一个整数的二进制有多少个1，就可以进行多少次这样的操作。

方法一: 与位运算
- 初始化数量统计变量res=0 。
- 循环逐位判断：当n=0 时跳出。
- res += n & 1 ：若n&1=1,则统计数res加一。
- n >>= 1 ： 将二进制数字n无符号右移一位
- 返回统计数量res

方法二: 库函数
- Integer.bitCount() 直接返回二进制中 1 的个数

## 参考代码
```Java
方法一：
public class Solution {
    public int hammingWeight(int n) {
        int res = 0;
        while(n != 0){
            res++;
            n = n&(n-1);
        }
        return res;
    }
}

方法二：
public class Solution {
    public int hammingWeight(int n) {
        return Integer.bitCount(n);
    }
}
```
