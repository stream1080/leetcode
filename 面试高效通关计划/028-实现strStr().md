# 028-实现strStr()

## [题目链接](https://leetcode-cn.com/problems/implement-strstr/)

## 解析

方法一：暴力匹配
- 让字符串needle与字符串haystack的所有长度为m的子串均匹配一次。
- 例如：hello 和 ll 进行匹配 只需要匹配长度之差次
- 为了减少不必要的匹配，我们每次匹配失败即立刻停止当前子串的匹配，对下一个子串继续匹配
- 如果当前子串匹配成功，我们返回当前子串的开始位置即可。如果所有子串都匹配失败，则返回−1。


方法二：KMP模式匹配


## 参考代码
```Java
方法一：暴力匹配
class Solution {
    public int strStr(String haystack, String needle) {
        int m = haystack.length();
        int n = needle.length();
        for(int i=0;i<=m-n;i++){
            boolean flag = true;
            for(int j=0;j<n;j++){
                //不相等则匹配失败，只需要匹配m-n次
                if(needle.charAt(j)!=haystack.charAt(i+j)){
                    flag = false;
                    break;
                }
            }
            if(flag) return i;
        }
        return -1;
    }
}
```