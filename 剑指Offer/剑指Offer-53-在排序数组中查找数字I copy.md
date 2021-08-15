# 剑指Offer-11-旋转数组的最小数字

## [题目链接](https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/)

## 解析

旋转数组是一个排序数组截取一部分后拼接到数组后面
例如：1，2，3，4，5  旋转后：3，4，5，1，2

方法一：二分查找
- 定义头尾双指针，遍历数组
- 如果mid大于当前区间的最大值，则说明最小值在mid后面
- 如果mid小于当前区间的最大值，则说明最小值在mid前面
- 我们可以去掉重复的数字，遍历结束后，left即为最小值


## 参考代码
```Java
class Solution {
    public int minArray(int[] numbers) {
        int left = 0,rigth = numbers.length-1;
        while(left<rigth){
            int mid = left + (rigth-left)/2;
            if(numbers[mid]>numbers[rigth])
                left = mid+1;
            else if(numbers[mid]<numbers[rigth])
                rigth = mid;
            else
                rigth--;//去重
        }
        return numbers[left];
    }
}
```