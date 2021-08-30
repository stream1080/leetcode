# 剑指Offer-33-二叉搜索树的后序遍历序列

## [题目链接](https://leetcode-cn.com/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/)

## 解析

方法一: 递归
- 定义递归返回值,p==j 返回true
- 划分左右子树,遍历后序数组,寻找第一个大于根节点的元素,记录索引m,划分左右子树(i,m-1)  (m,j-1),根为j
- recur(postorder,i,m-1)判断左子树是否正确
- recur(postorder,m,j-1)判断右子树是否正确

## 参考代码
```Java
方法一：
class Solution {
    public boolean verifyPostorder(int[] postorder) {
        return recur(postorder,0,postorder.length-1);
    }

    boolean recur(int[] postorder,int i,int j){
        if(i>=j) return true;
        int p = i;
        while(postorder[p] < postorder[j])
            p++;
        int m = p;
        while(postorder[p] > postorder[j])
            p++;
        return p == j && recur(postorder,i,m-1) && recur(postorder,m,j-1);
    }
}
```