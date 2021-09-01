# 剑指Offer-56-数组中数字出现的次数I

## [题目链接](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/)

## 解析

方法一：分组异或
- 遍历nums执行一次异或
- 在异或结果中找到任意为11的位,根据这一位对所有的数字进行分组。
- 拆分nums为两个子数组
- 分别遍历两个子数组执行异或
- 返回


## 参考代码
```Java
class Solution {
    public int[] singleNumbers(int[] nums) {
        int ret = 0;
        for(int n:nums)
            ret^=n;
        int div = 1;
        while((div & ret)==0)
            div<<=1;
        int a = 0,b = 0;
        for(int n:nums){
            if((div&n)!=0)
                a^=n;
            else
                b^=n;
        }
        return new int[]{a,b};
    }
}
```