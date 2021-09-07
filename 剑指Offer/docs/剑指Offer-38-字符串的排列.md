# 剑指Offer-38-字符串的排列

## [题目链接](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/)

## 解析

方法一：回溯



## 参考代码
```Java
class Solution {
    List<String> res;
    StringBuilder tmp;
    boolean[] visited;
    public String[] permutation(String s) {
        //全局变量初始化
        this.res = new ArrayList<String>();
        this.tmp = new StringBuilder();
        this.visited = new boolean[s.length()];

        char[] temp = s.toCharArray();
        Arrays.sort(temp);
        dfs(temp,0);
        return res.toArray(new String[0]);
    }

    public void dfs(char[] cs,int depth){
        if(depth == cs.length){
            res.add(tmp.toString());
            return;
        }
        for(int i = 0; i < cs.length; i++){
            if(i > 0 && cs[i - 1] == cs[i] && !visited[i - 1])  continue;
            if(!visited[i]) {
                tmp.append(cs[i]);
                visited[i] = true;
                dfs(cs,depth + 1);
                visited[i] = false;
                tmp.deleteCharAt(tmp.length() - 1);
            }
        }
    }
}
```