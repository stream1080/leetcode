# 剑指Offer-56-数组中数字出现的次数II

- [题目链接](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/)

## 解析

方法一：排序
- 题目限定条件，只有一个是出现一次的，其他的都是三次
- 排序后出现的情况有三种
- ABBBCCC 这种情况直接返回第一个
- BBBCCCA 这种情况直接返回最后一个
- BBBACCC 这种情况就需要判断
- 遍历排序后的数组，步长为三
- 如果nums[i] != nums[i+2] 则为i，否则为最后一个

方法二：Map存储出现次数
- 定义一个Map存储每个元素出现的次数
- 遍历Map，如果次数为1，则返回key

## 参考代码
```Java
方法一：
class Solution {
    public int singleNumber(int[] nums) {
        Arrays.sort(nums);
        for(int i=0;i<nums.length-2;i=i+3){
            if(nums[i] != nums[i+2])
                return nums[i];
        }
        return nums[nums.length-1];
    }
}
方法二：
class Solution {
    public int singleNumber(int[] nums) {
        Map<Integer,Integer> map = new HashMap<>();
        for(int i=0;i<nums.length;i++){
            map.put(nums[i],map.getOrDefault(nums[i],0)+1);
        }
        for(Integer i:map.keySet()){
            if(map.get(i) == 1)
                return i;
        }
        return -1;
    }
}
```
