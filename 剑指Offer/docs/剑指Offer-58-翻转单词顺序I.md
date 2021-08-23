# 剑指Offer-58-翻转单词顺序I

## [题目链接](https://leetcode-cn.com/problems/fan-zhuan-dan-ci-shun-xu-lcof/)

## 解析
方法一：双指针
- 由于String是不可变的，需要定义一个StringBuilder操作
- 定义双指针，都指向尾部
- i指针遍历到第一个单词开头，也就是空格处
- 截取字符串并加上空格，追加到StringBuilder上
- 跳过空格，让j和i到下一个单词
- 遍历结束后，转化为String并去掉空格，返回


## 参考代码
```Java
class Solution {
    public String reverseWords(String s) {
        s = s.trim();// 去掉首尾空格
        StringBuilder sb = new StringBuilder();
        int i = s.length()-1,j=i;
        while(i>=0){
            // 搜索首个空格，也就是最后一个单词
            while(i>=0 && s.charAt(i)!=' ') i--;
            sb.append(s.substring(i+1,j+1)+' ');// 单词末尾加上空格
            while(i>=0 && s.charAt(i)==' ') i--;// 跳过单词间的空格
            j=i;
        }
        // 转化String并去掉首尾空格
        return sb.toString().trim();
    }
}
```