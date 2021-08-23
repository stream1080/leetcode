# 剑指Offer-57-和为s的两个数字

## [题目链接](https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/)

## 解析
方法一：双指针
- 定义头尾双指针指向头尾
- 遍历数组，如果nums[left]+nums[right]>target，则尾指针向左才能靠近target
- 头指针反之亦然，返回结果

## 参考代码
```Java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int left = 0, right = nums.length-1;
        while(left<right){
            // 尾指针向左，靠近target
            if(nums[left]+nums[right]>target){
                right--;
            // 头指针向右，靠近target
            }else if(nums[left]+nums[right]<target){
                left++;
            }else   
                return new int[]{nums[left],nums[right]};
        }
        return new int[2];
    }
}
```