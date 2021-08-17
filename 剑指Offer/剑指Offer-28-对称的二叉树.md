# 剑指Offer-28-对称的二叉树

## [题目链接](https://leetcode-cn.com/problems/dui-cheng-de-er-cha-shu-lcof/)

## 解析

方法一：递归
- 使用递归函数，定义递归出口，如果L和R均为null。则对称
- 如果L和R仅一个为null，或者L和R值相等，则不对称
- 递归遍历L的左测和R的右侧(L.left,R.right) 和L的右测和R的左侧(L.right,R.left)
- 主函数，判断null是否为null，判断root的左右子树是否对称，返回结果


## 参考代码
```Java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        return root==null?true : isSymmetric(root.left,root.right);
    }

    public boolean isSymmetric(TreeNode L,TreeNode R){
        //左右相等，true
        if(L==null && R==null) return true;
        //左右不相等
        if(L==null || R==null || L.val != R.val) return false;
        //判断L的左测和R的右侧(L.left,R.right) 和L的右测和R的左侧(L.right,R.left)
        return isSymmetric(L.left,R.right) && isSymmetric(L.right,R.left);
    }
}
```