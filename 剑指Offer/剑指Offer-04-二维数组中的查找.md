# 剑指Offer-04-二维数组中的查找

## [题目链接](https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/)

## 解析、
题目要求在一个二维数组中查询一个target，这个二维数组是有序的，可以使用二分查找
```
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
target =  5，返回 true。
target = 20，返回 false。
```
- 使用双指针从右上角遍历二维数组
- 如果target大于当前值，则行号i++
- 如果target小于当前值，则列号j--
- 遍历结束后如果没找到，则返回false
- 需要注意一些边界条件的处理

## 参考代码
```Java
class Solution {
    public boolean findNumberIn2DArray(int[][] matrix, int target) {
        if(matrix.length==0 || matrix[0].length==0)
            return false;
        int i = 0,j=matrix[0].length-1;
        while(i<matrix.length && j>=0){
            //列号--
            if(matrix[i][j]>target)
                j--;
            //行号++
            else if(matrix[i][j]<target)
                i++;
            else
                return true;
        }
        return false;
    }
}
```