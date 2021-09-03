# 剑指Offer-57-和为s的连续正数序列II

## [题目链接](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/)

## 解析

方法一：双指针
- 定义双指针，从1开始，到target结束
- 如果sum>target,sum = sum-l,并且l右移
- 当窗口中数字和小于target时，r右移
- 如果sum = target,则加入结果集


## 参考代码
```Java
class Solution {
    public int[][] findContinuousSequence(int target) {
        List<int[]> list = new ArrayList<>();
        for(int l=1,r=1,sum = 0; r<target;r++){
            sum += r;
            while(sum > target){
                sum -= l++;
            }
            if(sum == target){
                int[] temp = new int[r-l+1];
                for(int i=0;i<temp.length;i++){
                    temp[i] = l+i;
                }
                list.add(temp);
            }
        }
        int[][] res = new int[list.size()][];
        for (int i = 0; i < res.length; i++) {
            res[i] = list.get(i);
        }
        return res;
    }
}
```