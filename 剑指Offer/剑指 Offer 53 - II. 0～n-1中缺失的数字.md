# 剑指 Offer 53 - II. 0～n-1中缺失的数字

## [题目链接](https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof/)

## 解析
方法一：数学
- 本题是排序的数组，而且数组元素是0到n-1
- 可以算出0到n-1的值，再减去数组实际的和
- 即为缺失的整数

方法二：二分查找
- 由于是有序数组，可以使用二分查找找到目标元素
- 若nums[mid]=mid则 “右子数组的首位元素” 一定在闭区间 [mid + 1, rigth]中，因此left = mid+1
- 若nums[mid]!=mid则 “左子数组的末位元素” 一定在闭区间 [left,mid—1]中，因此right = mid-1
- 遍历结束left的下标即为缺失的整数

## 参考代码
```Java
class Solution {
    public int missingNumber(int[] nums) {
        int left = 0,rigth = nums.length-1;
        while(left < rigth){
            int mid = left + (rigth-left)/2;
            if(nums[mid] == mid)
                left = mid+1;
            else
                rigth = mid-1;
        }
        return left;
    }
}
```