# 剑指Offer-56-数组中数字出现的次数II

## [题目链接](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)

## 解析
方法一：排序后遍历
- 排序后,相同的元素在一起,只有一个是单个的,其他都是三个
- 间隔一个元素进行对比,不相同则是单个元素,返回
- 有可能是最后一个,如果找不到不相同的就是最后一个

## 参考代码
```Java
方法一
class Solution {
    public int singleNumber(int[] nums) {
        Arrays.sort(nums);
        for(int i=0;i<nums.length-2;i=i+3){
            // 间隔一个进行对比
            if(nums[i] != nums[i+2])
                return nums[i];
        }
        // 否则是最后一个
        return nums[nums.length-1];
    }
}

```