# 剑指Offer-36-二叉搜索树与双向链表

## [题目链接](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)

## 解析
方法一：中序遍历
- 当节点 cur 为空，代表越过叶节点，直接返回；
- 递归遍历左子树，即 dfs(cur.left) ；
- 当pre 为空时： 代表正在访问链表头节点，记为 head ；
- 当pre不为空时： 修改双向节点引用，即 pre.right = cur ， cur.left = pre ；
- 保存 cur ： 更新 pre = cur ，即节点 cur 是后继节点的 pre ；
- 递归右子树，即 dfs(cur.right) ；
- 遍历结束后，头尾相连，返回头节点


## 参考代码
```Java
class Solution {
    Node pre = null,head = null;
    public Node treeToDoublyList(Node root) {
        if(root == null) return null;
        dfs(root);
        // 遍历结束后，头尾相连
        head.left = pre;
        pre.right = head;
        return head;
    }

    public void dfs(Node cur){
        if(cur == null) return ;
        dfs(cur.left);
        if(pre == null) 
            head = cur;
        else if(pre != null)
            pre.right = cur;
        cur.left = pre;
        pre = cur;
        dfs(cur.right);
    }
}
```