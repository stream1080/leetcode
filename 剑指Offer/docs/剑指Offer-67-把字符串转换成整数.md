# 剑指Offer-67-把字符串转换成整数

## [题目链接](https://leetcode-cn.com/problems/ba-zi-fu-chuan-zhuan-huan-cheng-zheng-shu-lcof/)

## 解析

方法一：遍历判断
- 先去掉头尾空格，判断去掉空格后的字符串
- 判断首字符是否为+或者-，标记后跳过
- 遍历字符串，如果当前字符为数字，进入循环，否则返回结果
- 获取当前字符的数字，判断是否越界
- 加入结果，进入下一轮循环，循环结束，根据正负标记返回结果

## 参考代码
```Java
方法一：
class Solution {
    public int strToInt(String str) {
        // 去掉头尾空格
        String s = str.trim();
        // 判断去掉空格后的字符串
        if(s.length() == 0) return 0;
        int i=0,res = 0,flag = 1;
        // 首字符位-，则为负数标记flag
        if(s.charAt(i) == '-') flag = -1;
        // 如果首字符为+或者-,跳过
        if(s.charAt(i) == '+' || s.charAt(i) == '-') i++;
        // 遍历字符串，如果当前字符为数字，进入循环，否则返回结果
        while(i<s.length() && Character.isDigit(s.charAt(i))){
            // 获取当前数字
            int num = s.charAt(i)-'0';
            // 处理越界
            if(res>Integer.MAX_VALUE/10 || (res == Integer.MAX_VALUE/10 && num>7))
                return flag>0?Integer.MAX_VALUE:Integer.MIN_VALUE;
            // 加入结果
            res = res*10 + num;
            i++;
        }
        return flag>0?res:-res;
    }
}
```