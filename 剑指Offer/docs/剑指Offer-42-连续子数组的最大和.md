# 剑指Offer-42-连续子数组的最大和

## [题目链接](https://leetcode-cn.com/problems/lian-xu-zi-shu-zu-de-zui-da-he-lcof/)

方法一：动态规划
- 本题求最大子序列和，可以使用动态规划
- 转移方程，f(n) = Max(f(n-1)+num[i],num[i])
- 需要一个pre保存当前元素之前的最大子序和
- 遍历数组，当前元素加上当前元素之前的最大子序和
- 更新pre，再更新max，返回结果


## 参考代码
```Java
dp数组
class Solution {
    public int maxSubArray(int[] nums) {
        int[] dp = new int[nums.length];
        dp[0] = nums[0];            // 初始化
        int max = nums[0];
        for(int i=1;i<nums.length;i++){
            dp[i] = Math.max(dp[i-1]+nums[i],nums[i]);
            max = Math.max(max,dp[i]); // 更新最大值
        }
        return max;
    }
}


滚动变量
class Solution {
    public int maxSubArray(int[] nums) {
        int pre=0,max = nums[0];//初始化，max未最大值
        for(int num:nums){
            //更新前n项数组和
            pre = Math.max(num,pre+num);
            //更新最大值
            max = Math.max(max,pre);
        }
        return max;
    }
}
```
