# 剑指Offer-12-矩阵中的路径

## [题目链接](https://leetcode-cn.com/problems/ju-zhen-zhong-de-lu-jing-lcof/)

## 解析

方法一：深度优先搜索


## 参考代码
```Java
class Solution {
    public boolean exist(char[][] board, String word) {
        for(int i=0;i<board.length;i++){
            for(int j=0;j<board[0].length;j++)
                if(dfs(board,word,0,i,j)) return true;
        }
        return false;
    }
    // 定义上下左右四个方向作为偏移数组
    int[] dx = new int[]{-1,0,1,0}, dy = new int[]{0,1,0,-1};
    public boolean dfs(char[][] board,String word,int u,int i,int j){
        // 定义出口，如果当前字母不相等，false
        if(board[i][j] != word.charAt(u)) return false;
        // 定义出口，如果长度一致，匹配成功
        if(u == word.length()-1) return true;
        char t = board[i][j];
        board[i][j] = '0'; //标记已经查找过的地方
        // 上下左右四个方向遍历
        for(int k=0;k<4;k++){
            int a = i+dx[k],b = j+dy[k];
            // 出界，或者已经查找过，跳出当前循环
            if(a<0||b<0||a>=board.length||b>=board[0].length||board[a][b]=='0') continue;
            if(dfs(board,word,u+1,a,b)) return true;
        }
        // 撤销之前的标记
        board[i][j] = t;
        return false;
    }
}
```