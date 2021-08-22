# 剑指Offer-63-股票的最大利润

## [题目链接](https://leetcode-cn.com/problems/gu-piao-de-zui-da-li-run-lcof/)

## 解析
本题可以维护一个变量，保存股票的历史最低价
方法一：遍历
- 遍历数组，保存股票历史最低价
- 同时根据历史最低价更新最大利润
- 返回结果


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
```