# 剑指Offer-55-二叉树的深度I

## [题目链接](https://leetcode-cn.com/problems/er-cha-shu-de-shen-du-lcof/)

## 解析

方法一：递归
- 递归法遍历左右子树的高度
- 返回左右子树的最高值，加上根节点1

方法二：迭代
- 使用一个队列进行层次遍历，每遍历一层，结果加一


## 参考代码
```Java
方法一：
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        // 遍历左右子树的高度
        int left = maxDepth(root.left);
        int right = maxDepth(root.right);
        // 返回左右子树的最高值，加上根节点1
        return Math.max(left,right) + 1;
    }
}

方法二：
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        int ans = 0;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);
        while(!queue.isEmpty()){
            LinkedList<TreeNode> tmp = new LinkedList<>();
            for(TreeNode node : queue){
                if(node.left != null) tmp.add(node.left);
                if(node.right != null) tmp.add(node.right);
            }
            ans++;
            queue = tmp;
        }
        return ans;
    }
}
```