# 剑指Offer-27-二叉树的镜像

## [题目链接](https://leetcode-cn.com/problems/er-cha-shu-de-jing-xiang-lcof/)

## 解析

方法一：递归
- 使用递归函数，定义递归出口，如果root为null。返回root
- 递归调用，获取当前节点的左节点
- 递归调用，获取当前节点的右节点
- 把右节点赋值左节点，把左节点赋值右节点
- 返回结果


## 参考代码
```Java
class Solution {
    public TreeNode mirrorTree(TreeNode root) {
        if(root==null) return root;
        //获取左节点
        TreeNode left = mirrorTree(root.left);
        //获取右节点
        TreeNode right = mirrorTree(root.right);
        root.left = right;//把右节点赋值左节点
        root.right = left;//把左节点赋值右节点
        return root;
    }
}
```