# 剑指Offer-51-数组中的逆序对

## [题目链接](https://leetcode-cn.com/problems/shu-zu-zhong-de-ni-xu-dui-lcof/)

## 解析

方法一: 分治排序

## 参考代码
```Java
方法一：
class Solution {
    int count = 0;
    int[] aux;
    public int reversePairs(int[] nums) {
        aux = new int[nums.length];
        sort(nums, 0, nums.length - 1);
        return count;
    }
    
    public void sort(int[] nums, int lo, int hi){
        if(hi <= lo)    return;
        
        int mid = (lo + hi) / 2;
        sort(nums, lo, mid);
        sort(nums, mid + 1, hi);
        
        merge(nums, lo, mid, hi);
    }

    private void merge(int[] nums, int lo, int mid, int hi) {
        int i = lo, j = mid + 1;
        for(int k = lo; k <= hi; k++)
            aux[k] = nums[k];
        
        int index = lo;
        while(i <= mid || j <= hi){
            if(i > mid)                 nums[index++] = aux[j++];
            else if(j > hi)             nums[index++] = aux[i++];
            else if(aux[i] <= aux[j])   nums[index++] = aux[i++];
            else                        {nums[index++] = aux[j++];  count += mid - i + 1;}
        }
    }
}
```