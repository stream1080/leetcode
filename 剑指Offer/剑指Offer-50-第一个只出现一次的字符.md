# 剑指Offer-50-第一个只出现一次的字符

## [题目链接](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

## 解析
本题可以使用哈希表存储每个字符出现的次数，然后遍历哈希表，然后次数为1的字符
这次我们不存储出现次数，因为只要求第一个出现一次的字符，我们存储boolean变量，出现两次以上的为false，返回true的字符即可

- 建立Map<Character,Boolean>
- 遍历字符串，出现两次以上存储为false
- 遍历Map，返回value为true的字符



## 参考代码
```Java
class Solution {
    public char firstUniqChar(String s) {
        Map<Character,Boolean> map = new HashMap<>();
        //出现两次以上的字符存储为false
        for(char ch:s.toCharArray()){
            map.put(ch,!map.containsKey(ch));
        }
        //遍历map，返回true的字符
        for(char ch:s.toCharArray()){
            if(map.get(ch))
                return ch;
        }
        return ' ';
    }
}
```