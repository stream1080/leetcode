# 剑指Offer-10-斐波那契数列I

## [题目链接](https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof/)

## 解析
这是一道斐波那契数列的题目，只不过他对结果进行了一个限定，处理一下结果即可
这次我们之间使用滚动数组，关于递归和动态规划请看这一篇[题解](https://github.com/stream1080/leetcode/blob/main/面试高效关计划/509-斐波那契数.md)

方法一：滚动数组
- 我们使用的是最近的结果，n-1和n-2，其他都浪费了
- 我们可以使用滚动数组，循环保存这三个变量，相互替代，循环使用
- 循环的同时我们对结果进行取余操作


## 参考代码
```Java
class Solution {
    public int fib(int n) {
        if(n==0 || n==1)
            return n;
        int p=0,q=1,r=0;
        for(int i=1;i<n;i++){
            //对结果取余
            r = (p+q)%1000000007;
            p = q;
            q = r;
        }
        return r;
    }
}
```