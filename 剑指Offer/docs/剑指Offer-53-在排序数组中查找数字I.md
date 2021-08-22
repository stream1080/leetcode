# 剑指Offer-53-在排序数组中查找数字I

## [题目链接](https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)

## 解析
方法一：二分查找
- 本题是排序的数组，所以可以之间遍历数组找到目标值
- 然后计数目标值出现的次数，返回结果
- 由于是有序数组，可以使用二分查找找到目标元素
- 然后再找目标元素出现的次数


## 参考代码
```Java
class Solution {
    public int search(int[] nums, int target) {
        int left = 0,right = nums.length-1;
        while(left<right){
            int mid = left + (right-left)/2;
            if(nums[mid]>=target)
                right = mid;
            else if(nums[mid]<target)
                left = mid+1;
        }
        //二分查找完成后，target的第一个元素索引为left
        int sum = 0;
        while(left<nums.length && nums[left++] == target)
            sum++;
        return sum;
    }
}
```