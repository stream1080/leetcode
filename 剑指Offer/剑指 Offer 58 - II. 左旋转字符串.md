# 剑指 Offer 58 - II. 左旋转字符串

## [题目链接](https://leetcode-cn.com/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/)

## 解析
方法一：截取+拼接
- 题目要求吧前n个字符放到字符串后面
- 我们可以直接截取n的后面的字符串
- 拼接n前面的字符串到后面，返回结果


方法二：循环拼接
- 与方法一类似，新建一个String变量
- 循环遍历n后面的字符放在String中
- 再遍历n前面的字符放到String后面


## 参考代码
```Java
方法一
class Solution {
    public String reverseLeftWords(String s, int n) {
        //截取n后面的放在前面，截取n前面的放在后面，拼接返回
        return s.substring(n)+s.substring(0,n);
    }
}

方法二：
class Solution {
    public String reverseLeftWords(String s, int n) {
        String str = new String();
        //拼接后面的
        for(int i=n;i<s.length();i++)
            str += s.charAt(i);
        //拼接前面
        for(int i=0;i<n;i++)
            str += s.charAt(i);
        return str;
    }
}
```