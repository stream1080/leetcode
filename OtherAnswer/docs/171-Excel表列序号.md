# 171-Excel表列序号

- [题目链接](https://leetcode-cn.com/problems/excel-sheet-column-number/)

## 解析
注：2021-10:09七牛云实习生一面
方法一：进制转换
- 类似26进制转换10进制，字符串有几位，则说明有几个进位
- 计算其代表的数值 num = 字母 - ‘A’ + 1
- 所以每遍历一位则ans = ans * 26 + num
- 以 ZY 为例，Z 的值为 26，Y 的值为 25，则结果为 26 * 26 + 25=701

## 参考代码
```Java
class Solution {
    public int titleToNumber(String columnTitle) {
        int sum = 0;
        for(int i=0;i<columnTitle.length();i++){
            sum = sum*26 + columnTitle.charAt(i)-'A'+1;
        }
        return sum;
    }
}
```
