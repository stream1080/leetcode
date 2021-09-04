# 剑指Offer-29-顺时针打印矩阵

## [题目链接](https://leetcode-cn.com/problems/shun-shi-zhen-da-yin-ju-zhen-lcof/)

## 解析

方法一：模拟
- 按照题目意思，先从左到右打印，从上到下
- 再从右到左，从下到上，顺时针打印数组
- i++是先赋值再加，++i是先加再赋值

## 参考代码
```Java
class Solution {
    public int[] spiralOrder(int[][] matrix) {
        if(matrix.length == 0) return new int[0];
        int l=0,r = matrix[0].length-1;// 列号
        int t=0,b = matrix.length-1 // 行号
        int x=0;// 结果数组的下标
        int[] res =new int[(r+1)*(b+1)];
        while(true){
            for(int i=l;i<=r;i++)
                res[x++] = matrix[t][i];
            if(++t > b) break;
            for(int i=t;i<=b;i++)
                res[x++] = matrix[i][r];
            if(l > --r) break;
            for(int i=r;i>=l;i--)
                res[x++] = matrix[b][i];
            if(t > --b) break;
            for(int i=b;i>=t;i--)
                res[x++] = matrix[i][l];
            if(++l > r) break;
        }
        return res;
    }
}
```