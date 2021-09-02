# 剑指Offer-39-数组中出现次数超过一半的数字

## [题目链接](https://leetcode-cn.com/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)

## 解析

方法一:排序
- 由于超过一半,则排序后中间的元素肯定是超过一半的元素

方法二:摩尔投票
- 票数统计 count = 0 , 众数 card;
- 遍历数组,当count为0时,假定当前数字num是众数；
- 当 num = card 时，票数 count + 1 ；当 num != card 时，票数-1 
- 返回card

## 参考代码
```Java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0,card = 0;
        for(int num:nums){
            if(count == 0)
                card = num;
            // 当 num==card 时,票数+1,当 num != card 时，票数-1 
            count += (card == num)?1:-1;
        }
        return card;
    }
}
```