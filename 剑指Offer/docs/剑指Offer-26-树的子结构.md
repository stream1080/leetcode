# 剑指Offer-26-树的子结构

## [题目链接](https://leetcode-cn.com/problems/shu-de-zi-jie-gou-lcof/)

## 解析
方法一：递归
- 使用递归函数，定义递归出口，如果A为null或者A.val不等于B.val,返回false
- 如果B为空，说明B已经访问完了。 返回true
- 先从根节点判断B是不是，如果不是再从左右子树判断
- 有一个是，则说明B是A的子结构




## 参考代码
```Java
class Solution {
    public boolean isSubStructure(TreeNode A, TreeNode B) {
    if (A == null || B == null)
        return false;
    //先从根节点判断B是不是A的子结构，如果不是在分别从左右两个子树判断，
    //只要有一个为true，就说明B是A的子结构
    return isSub(A, B) || isSubStructure(A.left, B) || isSubStructure(A.right, B);
}

    public boolean isSub(TreeNode A, TreeNode B) {
        //这里如果B为空，说明B已经访问完了，确定是A的子结构
        if (B == null)
            return true;
        //如果B不为空A为空，或者这两个节点值不同，说明B树不是
        //A的子结构，直接返回false
        if (A == null || A.val != B.val)
            return false;
        //当前节点比较完之后还要继续判断左右子节点
        return isSub(A.left, B.left) && isSub(A.right, B.right);
    }
}
```