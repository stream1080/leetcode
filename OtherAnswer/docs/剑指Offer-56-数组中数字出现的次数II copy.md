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
