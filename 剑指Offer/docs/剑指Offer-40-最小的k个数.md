# 剑指Offer-40-最小的k个数

## [题目链接](https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/)

## 解析
方法一：动态规划
- 排序后，选择前k位元素即可


## 参考代码
```Java
class Solution {
    public int[] getLeastNumbers(int[] arr, int k) {
        Arrays.sort(arr);
        int[] ans = new int[k];
        for(int i=0;i<k;i++){
            ans[i] = arr[i];
        }
        return ans;
    }
}
```