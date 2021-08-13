# 剑指 Offer 05. 替换空格

## [题目链接](https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/)



## 解析
- 由于String不可变性，我们无法直接操作String变量
- 所以我们需要新建一个可以操作的变量StringBuffer
- 遍历字符串s，如果遇到空格，就在StringBuffer追加%20
- 否则追加当前字符串中的当前字符
- 将StringBuffer转化成String后返回




## 参考代码
```Java
class Solution {
    public String replaceSpace(String s) {
        //新建一个可以操作的字符串变量
        StringBuffer sb = new StringBuffer();
        //遍历字符串
        for(int i=0;i<s.length();i++){
            //遇到空格则追加%20
            if(s.charAt(i)==' ')
                sb.append("%20");
            //否则用原来的
            else
                sb.append(s.charAt(i));
        }
        //转化后返回
        return sb.toString();
    }
}
```