# 028-实现strStr()

## [题目链接](https://leetcode-cn.com/problems/implement-strstr/)

## 解析

方法一：暴力匹配
- 让字符串needle与字符串haystack的所有长度为m的子串均匹配一次。
- 例如：hello 和 ll 进行匹配 只需要匹配长度之差次
- 为了减少不必要的匹配，我们每次匹配失败即立刻停止当前子串的匹配，对下一个子串继续匹配
- 如果当前子串匹配成功，我们返回当前子串的开始位置即可。如果所有子串都匹配失败，则返回−1。


方法二：KMP模式匹配
- 编写构造next数组的函数getNext(),形成前缀表
- 前缀表是用来回退的，它记录了模式串与主串(文本串)不匹配的时候，模式串应该从哪里开始重新匹配。
- 遍历文本串，文本串与模式串进行一一匹配，如果匹配成功，则继续往后
- 如果匹配失败，则根据next数组进行回退，继续匹配
- 如果匹配结束，并且j==n,说明全部匹配成功，返回i-n+1，是起始位置
- 否则匹配失败，返回-1；


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
方法二：KMP算法
class Solution {
    public int strStr(String haystack, String needle) {
        int m = haystack.length(),n = needle.length();
        if(n==0) return 0;
        int[] next = new int[n];
        getNext(next,needle);//构造next数组
        for(int i=0,j=0;i<m;i++){
            //不匹配，通过next数组向前回溯
            while(j>0 && haystack.charAt(i) != needle.charAt(j))
                j = next[j-1];
            //匹配成功，指针往后移一位
            if(haystack.charAt(i) == needle.charAt(j))
                j++;
            //j指针移到needle结尾，匹配结束，返回
            if(j==n) return i-n+1;
        }
        return -1;
    }
    //求next数组
    public void getNext(int[] next,String s){
        //初始条件i为后缀开始位置; j为前缀开始位置，也代表了前缀的长度
        for(int i=1,j=0;i<s.length();i++){
            //前后缀不相等，向前回溯
            while(j>0 && s.charAt(i)!=s.charAt(j))
                j = next[j-1];
            //前后缀相等，j往后
            if(s.charAt(i) == s.charAt(j))
                j++;
            next[i] = j;//更新next数组
        }
    }
}
```