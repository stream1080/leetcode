# 剑指Offer-15-二进制中1的个数

## [题目链接](https://leetcode-cn.com/problems/er-jin-zhi-zhong-1de-ge-shu-lcof/)


## 方法一：哈希表

方法一:与位运算

- 初始化数量统计变量res=0 。
- 循环逐位判断：当n=0 时跳出。
- res += n & 1 ：若n&1=1,则统计数res加一。
- n >>= 1 ： 将二进制数字n无符号右移一位
- 返回统计数量res

## 参考代码
```Java
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
```
