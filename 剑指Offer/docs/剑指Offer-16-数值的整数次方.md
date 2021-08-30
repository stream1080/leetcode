# 剑指Offer-16-数值的整数次方

## [题目链接](https://leetcode-cn.com/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/)

## 解析

方法一：快速幂
- 向下整除 n/2 等价于右移一位n>>1
- 取余数n%2等价于判断二进制最右一位值n&1
- 当x=0时,直接返回0,否则初始化res=1;
- 当n<0时,把负数转化成正数,即x=1/x,n=-n;
- 循环计算,当n=0时,跳出循环,否则当n&1 = 1时,res*=x
- x*=x,n>>=1,循环结束返回res

## 参考代码
```Java
方法一：
class Solution {
    public double myPow(double x, int n) {
        if(x==0) return 0;
        long b = n;
        double res = 1.0;
        // 如果是负数,转化成正数
        if(n<0){
            x = 1/x;
            b = -b;
        }
        while(b > 0) {
            if((b & 1) == 1) 
                res *= x;
            x *= x;
            b >>= 1;
        }
        return res;
    }
}
```