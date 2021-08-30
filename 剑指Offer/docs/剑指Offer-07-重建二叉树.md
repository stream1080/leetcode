# 剑指Offer-07-重建二叉树

## [题目链接](https://leetcode-cn.com/problems/zhong-jian-er-cha-shu-lcof/)

## 解析

方法一：递归+分治

- 前序遍历:[根节点 | 左子树 | 右子树 ] 排序
- 中序遍历:[左子树 | 根节点 | 右子树 ] 排序
- 前序遍历的第一个元素为树的根节点 node 
- 在中序遍历中搜索根节点 node 的索引,可将 中序遍历 划分为 [ 左子树 | 根节点 | 右子树 ]
- 根据中序遍历中的左 / 右子树的节点数量,可将 前序遍历 划分为 [ 根节点 | 左子树 | 右子树 ]
- 递归终止条件, 当 left > right时,代表已经越过叶节点，此时返回null

## 参考代码
```Java
class Solution {
    HashMap<Integer,Integer> map = new HashMap<>();
    int[] preorder;

    public TreeNode buildTree(int[] preorder, int[] inorder) {
        this.preorder = preorder;
        for(int i=0;i<inorder.length;i++)
            map.put(inorder[i],i);
        return recur(0,0,inorder.length-1);
    }

    public TreeNode recur(int pre_root,int in_left,int in_right){
        if(in_left > in_right)
            return null;
        TreeNode root = new TreeNode(preorder[pre_root]);
        int idx = map.get(preorder[pre_root]);
        root.left = recur(pre_root+1,in_left,idx-1);
        root.right = recur(pre_root + (idx - in_left) + 1,idx+1,in_right);
        return root;
    }
}
```

