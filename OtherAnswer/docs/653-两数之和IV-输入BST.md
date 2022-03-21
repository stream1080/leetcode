# 653-两数之和IV-输入BST

- [题目链接](https://leetcode-cn.com/problems/two-sum-iv-input-is-a-bst/)

## 解析

方法一：哈希表+深度优先遍历
- 类似两数之和，建立一个哈希表，存储遍历过的节点值
- 递归遍历，如果哈希表存在 k-root.val 的值，则 true；
- 递归遍历左右节点

## 参考代码
```Java
class Solution {
    Set<Integer> set = new HashSet<>();
    public boolean findTarget(TreeNode root, int k) {
        if(root == null) return false;
        if(set.contains(k-root.val)) return true;
        set.add(root.val);
        return findTarget(root.left,k) || findTarget(root.right,k);
    }
}
```
