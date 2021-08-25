# 剑指Offer-54-二叉搜索树的第k大节点

## [题目链接](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-di-kda-jie-dian-lcof/)

## 解析
方法一：中序遍历
- 由于题目给的二叉树是二叉搜索树，中序遍历后的序列就是递增的
- 可以定义一个List，存储中序遍历，返回倒数第k个节点
- 中序遍历是左根右，我们可以改变遍历顺序，右根左
- 使用计数器，返回第k给节点，即为第k大的元素


## 参考代码
```Java
class Solution {
    int ans = 0, count = 0;
    public int kthLargest(TreeNode root, int k) {
        dfs(root,k);
        return ans;
    }

    public void dfs(TreeNode root,int k){
        if(root == null) return ;
        // 右根左遍历
        dfs(root.right,k);
        // 计数器，记录遍历到第几个
        if(++count == k)
            ans = root.val;
        dfs(root.left,k);
    }
}
```