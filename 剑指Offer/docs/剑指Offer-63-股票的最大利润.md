# 剑指Offer-63-股票的最大利润

## [题目链接](https://leetcode-cn.com/problems/gu-piao-de-zui-da-li-run-lcof/)

## 解析
本题可以维护一个变量，保存股票的历史最低价
方法一：遍历
- 遍历数组，保存股票历史最低价
- 同时根据历史最低价更新最大利润
- 返回结果

方法二：动态规划
- dp[i][0]表示第i天持有股票所得的最多现金
- dp[i][1]表示第i天不持有股票所得的最多现金
- 递推 第i天买入股票，所得现金就是买入股票后的现金-prices[i];
- 与昨天持有股票所得的现金dp[i-1][0],取最大值
- 若第i天卖出股票，所获现金就是，股票价格prices[i]+dp[i-1][1]
- 与昨天对比，取最大值

## 参考代码
```Java
class Solution {
    public int maxProfit(int[] prices) {
        if(prices.length==0) return 0;
        int min = prices[0],max = 0;
        for(int price:prices){
            // 保存历史最低价
            min = Math.min(min,price);
            // 更新最大利润
            max = Math.max(max,price-min);
        }
        return max;
    }
}

方法二：动态规划
class Solution {
    public int maxProfit(int[] prices) {
        int[][] dp = new int[prices.length][2];
        dp[0][0] -= prices[0]; 
        dp[0][1] = 0; 
        for(int i=1;i<prices.length;i++){
            // 第i天持有股票
            dp[i][0] = Math.max(dp[i-1][0],-prices[i]);
            // 第i天卖出股票
            dp[i][1] = Math.max(dp[i-1][1],prices[i] + dp[i-1][0]);
        }
        return dp[prices.length-1][1];
    }
}
```