# 剑指Offer-55-平衡二叉树II

## [题目链接](https://leetcode-cn.com/problems/ping-heng-er-cha-shu-lcof/)

## 解析

方法一：递归
- 递归遍历左右子树的高度，对比绝对值是否<=1
- 继续向下递归遍历，返回结果

## 参考代码
```Java
方法一：
class Solution {
    public boolean isBalanced(TreeNode root) {
        if(root == null) return true;
        // 对比左右子树的高度
        return Math.abs(dfs(root.left) - dfs(root.right)) <= 1 && isBalanced(root.left) && isBalanced(root.right);

    }
    // 递归遍历子树的高度
    public int dfs(TreeNode root){
        if(root == null) return 0;
        int left = dfs(root.left);
        int right = dfs(root.right);
        return Math.max(left,right)+1;
    }
}

```