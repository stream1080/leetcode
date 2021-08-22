# 剑指Offer-10-青蛙跳台阶问题II

## [题目链接](https://leetcode-cn.com/problems/qing-wa-tiao-tai-jie-wen-ti-lcof/)

## 解析
这一题和上一题[斐波那契数列](https://github.com/stream1080/leetcode/blob/main/剑指Offer/剑指Offer-10-斐波那契数列I)解法基本一致，仅初始条件不同

方法一：滚动数组
- 我们使用的是最近的结果，n-1和n-2，其他都浪费了
- 我们可以使用滚动数组，循环保存这三个变量，相互替代，循环使用
- 循环的同时我们对结果进行取余操作


## 参考代码
```Java
class Solution {
    public int numWays(int n) {
        if(n<2) return 1;
        int p=1,q=1,r=0;
        for(int i=1;i<n;i++){
            r = (p+q)%1000000007;
            p = q;
            q = r;
        }
        return r;
    }
}
```