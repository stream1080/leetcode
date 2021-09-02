# 剑指Offer-66-构建乘积数组

## [题目链接](https://leetcode-cn.com/problems/gou-jian-cheng-ji-shu-zu-lcof/)

## 解析

方法一：遍历
- 初始化：数组b,其中b[0] = 1,辅助变量tmp=1
- 计算b[i]的下三角各元素的乘积,直接乘入b[i],
- 计算b[i]的上三角各元素的乘积,记为tmp,并乘入b[i]
- 返回b


## 参考代码
```Java
方法一：
class Solution {
    public int[] constructArr(int[] a) {
        int[] b = new int[a.length];
        if(a.length == 0) return b;
        b[0] = 1;
        int tmp = 1;
        for(int i=1;i<a.length;i++){
            b[i] = b[i-1]*a[i-1];
        }
        for(int i=a.length-2;i>=0;i--){
            tmp *= a[i+1];
            b[i] *= tmp;
        }
        return b;
    }
}
```