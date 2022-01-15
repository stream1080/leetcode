# 剑指Offer-62-圆圈中最后剩下的数字

## [题目链接](https://leetcode-cn.com/problems/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/)

## 解析
方法一：数学
- 当只有一个的时候,下标为零
- 每多一人,胜利者下标相当于往右挪动了m位
- 再对当前人数取模求得新的胜利者下标

方法二：模拟
- 建立一个list，存放各个元素，
- 遍历list，数到m的元素移除
- 返回最后剩下的元素

## 参考代码
```Java
方法一
class Solution {
    public int lastRemaining(int n, int m) {
        int ans = 0; //当只有一个的时候,下标为零
        // 每多一人,胜利者下标相当于往右挪动了m位
        // 再对当前人数取模求得新的胜利者下标
        for(int i=2;i<=n;i++){
            ans = (ans + m) % i;
        }
        return ans;
    }
}

方法二：
class Solution {
    public int lastRemaining(int n, int m) {
        List<Integer> list = new ArrayList<>();
        for(int i=0;i<n;i++)
            list.add(i);
        int idx = 0;
        while(n>1){
            idx = (idx+m-1)%n;
            list.remove(idx);
                n--;
        }
        return list.get(0);
    }
}
```