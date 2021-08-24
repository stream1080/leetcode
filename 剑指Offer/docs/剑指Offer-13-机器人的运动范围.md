# 剑指Offer-13-机器人的运动范围

## [题目链接](https://leetcode-cn.com/problems/ji-qi-ren-de-yun-dong-fan-wei-lcof/)

## 解析

方法一：深度优先搜索
- 递归终止条件：数组下标越界，或者元素被访问过，或者坐标位数和大于k, 直接返回0，表示该元素无效或者不能到达。
- 每次递归都返回当前位置数(1)+相邻方向上的可达位置数。


## 参考代码
```Java
class Solution {
    public int movingCount(int m, int n, int k) {
        // 设置标记数组，标记元素是否访问过
        boolean[][] flag = new boolean[m][n];
        // 图的dfs，起始点只有一个，因此只要从原点进行DFS即可
        return dfs(m,n,k,0,0,flag);
    }
    public int dfs(int m, int n, int k, int x, int y, boolean[][] flag){
        // 如果下标越界,该当前位置元素已经被访问过或者数位和大于k，则返回 0，结束递归
        if(x < 0 || y < 0 || x >= m || y >= n || flag[x][y] || x/10+x%10+y/10+y%10 > k)
            return 0;
        // 如果该位置元素可达，就将标记位设置为 true
        flag[x][y] = true;
        
        // 继续统计各个方向的可访问位置
        return dfs(m,n,k,x+1,y,flag) + dfs(m,n,k,x,y+1,flag) + 1;
    }
}

```