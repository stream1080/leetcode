# 剑指Offer-34-二叉树中和为某一值的路径

## [题目链接](https://leetcode-cn.com/problems/er-cha-shu-zhong-he-wei-mou-yi-zhi-de-lu-jing-lcof/)

## 解析
方法一：深度优先遍历
- 定义一个List用于存放结果，LinkedList用于存放每个路径
- 由于需要回溯，使用队列，可以方便删除最后一个元素
- 深度优先搜索，每次搜索前target -= root.val
- 搜索到叶子节点，并且路径和等于target，加入结果集
- 遍历左右节点，回溯，删除最后一个节点
- 遍历结束，返回结果

## 参考代码
```Java
class Solution {
    List<List<Integer>> list = new ArrayList<>();
    // 由于需要回溯，使用队列，可以方便删除最后一个元素
    Deque<Integer> tmp = new LinkedList<>();
    public List<List<Integer>> pathSum(TreeNode root, int target) {
        dfs(root,target);
        return list;
    }
    public void dfs(TreeNode root,int target){
        if(root == null) return ;
        tmp.add(root.val);
        target -= root.val;
        // 搜索到叶子节点，并且路径和等于target，加入结果集
        if(root.left == null && root.right == null && target == 0)
            list.add(new LinkedList<Integer>(tmp));
        // 遍历左右节点
        dfs(root.left,target);
        dfs(root.right,target);
        // 回溯，删除最后一个节点
        tmp.removeLast();
    }
}
```