# 剑指Offer-03-数组中重复的数字

## [题目链接](https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)

## 解析

方法一：排序

- 找数组中的重复元素，题目要求只返回一个就可以
- 我们可以对数组进行排序，排序后，重复元素一定是相邻的
- 遍历数组，如果i和i+1的元素相等，返回结果

方法二：集合

- 看到重复元素，我们可以想到集合Set的特性，无序不重复
- 遍历数组，将数组元素添加到Set中
- 如果添加失败，则为重复元素，返回结果即可

方法三：原地置换

- 本题有一个条件，数组元素在0到n-1之间，则说明索引与元素是一对多的关系
- 遍历数组并通过交换操作，使索引与值一一对应
- 如果 num[i] == i,则是一一对应，无须交换
- 如果nums[nums[i]] == nums[i] ,找到一组重复值，之间返回
- 否则交换索引i和nums[i]的值

## 参考代码
```Java
方法一：
class Solution {
    public int findRepeatNumber(int[] nums) {
        Arrays.sort(nums);
        for(int i=0;i<nums.length-1;i++){
            if(nums[i]==nums[i+1])
                return nums[i];
        }
        return -1;
    }
}

方法二
class Solution {
    public int findRepeatNumber(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for(int num:nums){
            //添加失败返回结果
            if(!set.add(num))
                return num;
        }
        return -1;
    }
}
方法三：
class Solution {
    public int findRepeatNumber(int[] nums) {
        int i = 0;
        while(i<nums.length){
            //跳过
            if(nums[i] == i){
                i++;
                continue;
            //重复元素
            }else if(nums[nums[i]]==nums[i])
                return nums[i];
            //交换
            else{
                int temp = nums[i];
                nums[i] = nums[temp];
                nums[temp] = temp;
            }
        }
        return -1;
    }
}
```

