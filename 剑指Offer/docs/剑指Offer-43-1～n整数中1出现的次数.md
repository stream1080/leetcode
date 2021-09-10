# 剑指Offer-43-1～n整数中1出现的次数

## [题目链接](https://leetcode-cn.com/problems/1nzheng-shu-zhong-1chu-xian-de-ci-shu-lcof/)


## 方法一：哈希表

方法一:动态规划-内存超限
- 定义dp数组，dp[i]代表i的1的个数
- 初始化dp[1]=1,1的i的个数为1
- 递推，dp[i] = dp[i % 10] + dp[i / 10];，并且累加结果
- 返回

## 参考代码
```Java
class Solution {
    public int countDigitOne(int n) {
        int ans = 0;
        int[] dp = new int[n + 1];
        dp[1] = 1;
        for (int i = 1; i <= n; i++) {
            dp[i] = dp[i % 10] + dp[i / 10];
            ans += dp[i];
        }
        return ans;
    }
}
```
