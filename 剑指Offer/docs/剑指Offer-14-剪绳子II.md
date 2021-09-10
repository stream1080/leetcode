# 剑指Offer-14-剪绳子II

## [题目链接](https://leetcode-cn.com/problems/jian-sheng-zi-ii-lcof/)

## 解析

方法一：贪心
- 绳子段切分的越多，乘积越大，且3做因数比2更优。
- 不断剪去 长度3 并用sum累乘
- 循环结束的三种情况：
   - n=n-3==2 
n长度剩下2，因 n > 4 跳出循环，return 乘积为sum*2。
   - n=n-3==3 
长度刚好可以被剪完，因 n > 4 跳出循环，return 乘积为sum*3。
  - n=n-3==4 
再剪一次的话，长度剩下1，则最后一段绳子长度为 1； 需要把最后的 3 和 1 替换为 2 和 2，因为 2 * 2 > 3 * 1； 因 n > 4 跳出循环，return 乘积 sum*4 即可。

- 综上,最后返回 res*n 对1000000007取余即可

## 参考代码
```Java
class Solution {
    public int cuttingRope(int n) {
        if(n<=3) return n-1;
        long res = 1;
        while(n>4){
            res *=3;
            res = res % 1000000007;
            n -= 3;
        }
        return (int)(res * n % 1000000007);
    }
}
```