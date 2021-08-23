# 剑指Offer-21-调整数组顺序使奇数位于偶数前面

## [题目链接](https://leetcode-cn.com/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

## 解析
方法一：双指针
- 定义首尾两个指针，分别指向头和尾
- 头指针从左往右遍历，遇到偶数停下
- 尾指针从右往左遍历，遇到奇数停下
- 交换两个值，返回结果


## 参考代码
```Java
class Solution {
    public int[] exchange(int[] nums) {
        int left = 0,rigth = nums.length-1;
        while(left<rigth){
            // 头指针找到偶数
            while(left<rigth && nums[left]%2==1){
                left++;
            }
            // 尾指针找到奇数
            while(left<rigth && nums[rigth]%2==0){
                rigth--;
            }
            //交换
            int tmp = nums[left];
            nums[left] = nums[rigth];
            nums[rigth] = tmp;
        }
        return nums;
    }
}
```