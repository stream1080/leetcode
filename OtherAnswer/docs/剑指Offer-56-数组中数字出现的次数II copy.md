# 492-构造矩形

- [题目链接](https://leetcode-cn.com/problems/construct-the-rectangle/)

## 解析

方法一：双指针
- 先对面积开方，取int型整数t
- 定义双指针为t，向两边扩散
- 如果i*j >= area,则左指针向左
- 如果i*j <= area,则右指针向右
- 如果i*j == area,则返回结果

方法二：数学
- L * W = area，这也意味着area可以被W整除；
- L >= M 则W*W < L * W,则只需要满足w被area整除，并且w<根号area
- 定义w为根号area的整除，当w不能被area整除，则w--；循环 
- 否则，返回结果area/w，w

## 参考代码
```Java
方法一：
class Solution {
    public int[] constructRectangle(int area) {
        int i = (int)Math.sqrt(area); 
        int j = i;
        while(i<=j){
            if(i*j == area ){
                return new int[]{j,i};
            }else if(i*j > area) i--;
            else if(i*j < area) j++;
        }
        return new int[]{0,0};
    }
}
方法二：
class Solution {
    public int[] constructRectangle(int area) {
        int w = (int)Math.sqrt(area);
        while(area % w != 0){
            w--;
        }
        return new int[]{area/w,w};
    }
}
```
