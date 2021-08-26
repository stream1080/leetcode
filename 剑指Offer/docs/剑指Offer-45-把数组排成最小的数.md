# 剑指Offer-45-把数组排成最小的数

## [题目链接](https://leetcode-cn.com/problems/ba-shu-zu-pai-cheng-zui-xiao-de-shu-lcof/)

## 解析
方法一：文本排序
- 文本排序，例如3和30，
- 如果"3"+"30">"30"+"3"则"3">"30"
- 排序后输出


## 参考代码
```Java
class Solution {
    public String minNumber(int[] nums) {
        List<String> list = new ArrayList<>();
        for(int num:nums){
            list.add(String.valueOf(num));
        }
        // 文本排序，如果"3"+"30">"30"+"3"则"3">"30"
        list.sort((a,b)->(a+b).compareTo(b+a));
        return String.join("",list);
    }
}
```