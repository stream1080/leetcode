# 剑指Offer-49-丑数

## [题目链接](https://leetcode-cn.com/problems/chou-shu-lcof/)

## 解析

方法一：动态规划
- 丑数只包含因子2,3,5因此丑数=某较小丑数×某因子
- 定义dp数组，dp[i] 表示第i+1个丑数 初始状态dp[0] = 1
- 当三指针id2，id3，id5满足一下条件时，dp[i] 为三种情况的最小值
- 



## 参考代码
```Java
class Solution {
    public int nthUglyNumber(int n) {
        if(n<=0) return -1;
        int[] dp = new int[n];
        dp[0] = 1;
        int id2 = 0,id3 = 0,id5 = 0; 
        for(int i=1;i<n;i++){
            dp[i] = Math.min(dp[id2]*2,Math.min(dp[id3]*3,dp[id5]*5));
            if(dp[id2]*2 == dp[i])
                id2++;
            if(dp[id3]*3 == dp[i])
                id3++;
            if(dp[id5]*5 == dp[i])
                id5++;
        }
        return dp[n-1];
    }
}
```