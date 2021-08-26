# 剑指Offer-61-扑克牌中的顺子

## [题目链接](https://leetcode-cn.com/problems/bu-ke-pai-zhong-de-shun-zi-lcof/)

## 解析
方法一：排序
- 先排序，然后遍历数组
- 统计0的个数，并且统计前后两数(大于1)的差值
- 最后对比0的个数和差值

## 参考代码
```Java
class Solution {
    public boolean isStraight(int[] nums) {
        Arrays.sort(nums);
        int zeroSum = 0 , diff = 0;
        for(int i=1;i<nums.length;i++){
            // 统计0的个数
            if(nums[i-1] == 0)
                zeroSum++;
            else{
                // 有相等的肯定不为顺子
                if(nums[i]==nums[i-1]) return false;
                // 计算前后两个数之差
                if(nums[i]-nums[i-1]!=1)
                    diff += nums[i]-nums[i-1]-1;
            }
        }
        // 对比0的个数和差值
        return zeroSum>=diff;
    }
}
```