# 剑指Offer-37-序列化二叉树

## [题目链接](https://leetcode-cn.com/problems/xu-lie-hua-er-cha-shu-lcof/)

## 解析
方法一：抖机灵

方法二：
- 

## 参考代码
```Java
public class Codec {

    private TreeNode root;
    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        this.root = root;
        return null;
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        return root;
    }
}
```