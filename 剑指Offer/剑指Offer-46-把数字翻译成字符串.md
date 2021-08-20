# 剑指Offer-46-把数字翻译成字符串

## [题目链接](https://leetcode-cn.com/problems/ba-shu-zi-fan-yi-cheng-zi-fu-chuan-lcof/)

## 解析
方法一：动态规划
- 翻译情况有两种，一种是当数子是0，1，2这种，结果是a,b,c
- 另一种情况是12，30这种，12可以翻译，40不能翻译
- 如果第i−1位和第i位组成的数字在10到25之间，可以把这两位连起来翻译
- 转移方程，当x在10-25之间时f(i) = f(i-1) + f(i-2)
- 单独一位翻译时：f(i) = f(i-1);

方法二：滚动数组
- 暂无


## 参考代码
```Java
class Solution {
    public int translateNum(int num) {
        String s = String.valueOf(num);
        int[] dp = new int[s.length()+1];
        dp[0]=dp[1]=1;
        for(int i=2;i<=s.length();i++){
            //截取两位，每次翻译两位
            String tmp = s.substring(i-2,i);
            if(tmp.compareTo("10")>=0 && tmp.compareTo("25")<=0)
                dp[i] = dp[i-1]+dp[i-2];
            else
                dp[i] = dp[i-1];
        }
        return dp[s.length()];
    }
}
```