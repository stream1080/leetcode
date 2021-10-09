# 168-Excel表列名称

- [题目链接](https://leetcode-cn.com/problems/excel-sheet-column-title/)

## 解析

方法一：
- 高位的一定是26的整数倍. 推理出. 最低位一定是26模的余数. 
- 如果低位余数为0. 但是对于其表示方法. 不进位的表示中, 26不用 A0表示.而是使用 0Z表示.(实际0省略).因此对于没有余数的情况下.如果 x > 26 ,那低位一定是Z
- 处理完低位后,再说次低位. 把个位的数抹掉后. 高位的数一定是26的整数倍. 那高位的数 / 26. 那又回到了个位的处理方式.
- 循环2的处理.直到结束.

## 参考代码
```Java
方法一：
class Solution {
    public String convertToTitle(int columnNumber) {
        StringBuilder sb = new StringBuilder();
        while(columnNumber > 0){
            int tmp = columnNumber % 26;
            if(tmp > 0){
                sb.append((char)('A'+tmp-1));
                columnNumber = columnNumber / 26;
            }else{
                sb.append("Z");
                columnNumber = (columnNumber-26)/26;
            }
        }
        return sb.reverse().toString();
    }
}
方法二：
class Solution {
    public String convertToTitle(int columnNumber) {
        if(columnNumber<=0)
            return "";
        StringBuilder sb = new StringBuilder();
        while(columnNumber>0){
            columnNumber--;
            sb.append((char)(columnNumber%26+'A'));
            columnNumber = columnNumber/26;
        }
        return sb.reverse().toString();
    }
}
```
