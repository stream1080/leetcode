# 剑指Offer-63-股票的最大利润

## [题目链接](https://leetcode-cn.com/problems/gu-piao-de-zui-da-li-run-lcof/)

## 解析
本题可以维护一个变量，保存股票的历史最低价
方法一：遍历
- 遍历数组，保存股票历史最低价
- 同时根据历史最低价更新最大利润
- 返回结果


## 参考代码
```Java
class Solution {
    public char firstUniqChar(String s) {
        Map<Character,Boolean> map = new HashMap<>();
        //出现两次以上的字符存储为false
        for(char ch:s.toCharArray()){
            map.put(ch,!map.containsKey(ch));
        }
        //遍历map，返回true的字符
        for(char ch:s.toCharArray()){
            if(map.get(ch))
                return ch;
        }
        return ' ';
    }
}
```