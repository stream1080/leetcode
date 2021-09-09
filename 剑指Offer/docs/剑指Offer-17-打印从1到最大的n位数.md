# 剑指Offer-17-打印从1到最大的n位数

## [题目链接](https://leetcode-cn.com/problems/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/)

## 解析

方法一：遍历
- 先计算有多少位，10的n次方-1
- 定义结果数组，遍历存放，返回

## 参考代码
```Java
class Solution {
    public int[] printNumbers(int n) {
        int m = 1;
        // 计算位数
        for(int i=0;i<n;i++){
            m *=10;
        }
        int[] res = new int[m-1];
        for(int i=0;i<m-1;i++){
            res[i] = i+1;
        }
        return res;
    }
}
```