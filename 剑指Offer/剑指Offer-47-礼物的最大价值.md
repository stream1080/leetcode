# 剑指Offer-47-礼物的最大价值

## [题目链接](https://leetcode-cn.com/problems/li-wu-de-zui-da-jie-zhi-lcof/)

## 解析

方法一：动态规划
- 本题中，只允许往右和往下取礼物，
- 定义dp[i][j]表示从矩阵的左上角走到坐标（i，j）所能拿到的最大礼物。
- 遍历表格，取左边和上边的礼物，取最大值。加上左上角的值，更新dp[i][j];
- 遍历结束，返回结果


## 参考代码
```Java
class Solution {
    public int maxValue(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[][] dp = new int[m+1][n+1];
        for(int i=1;i<=m;i++){
            for(int j=1;j<=n;j++){
                dp[i][j] = Math.max(dp[i-1][j],dp[i][j-1]) + grid[i-1][j-1];
            }
        }
        return dp[m][n];
    }
}
```