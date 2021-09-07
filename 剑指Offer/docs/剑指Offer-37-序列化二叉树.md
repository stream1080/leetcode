# 剑指Offer-37-序列化二叉树

## [题目链接](https://leetcode-cn.com/problems/xu-lie-hua-er-cha-shu-lcof/)

## 解析
方法一：抖机灵

方法二：层次遍历
- 

## 参考代码
```Java
public class Codec {

    private TreeNode root;

    public String serialize(TreeNode root) {
        this.root = root;
        return null;
    }

    public TreeNode deserialize(String data) {
        return root;
    }
}
方法二：
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        if(root == null) return "[]";
        StringBuilder res = new StringBuilder("[");
        Queue<TreeNode> queue = new LinkedList<>(){{add(root);}};
        while(!queue.isEmpty()){
            TreeNode node = queue.poll();
            if(node != null){
                res.append(node.val+",");
                queue.add(node.left);
                queue.add(node.right);
            }
            else
                res.append("null,");
        }
        res.deleteCharAt(res.length()-1);
        res.append("]");
        return res.toString();
    }

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        if(data.equals("[]")) return null;
        String[] vals = data.substring(1,data.length()-1).split(",");
        TreeNode root = new TreeNode(Integer.parseInt(vals[0]));
        Queue<TreeNode> queue = new LinkedList<>() {{add(root);}};
        int i = 1;
        while(!queue.isEmpty()){
            TreeNode node = queue.poll();
            if(!vals[i].equals("null")){
                node.left = new TreeNode(Integer.parseInt(vals[i]));
                queue.add(node.left);
            }
            i++;
            if(!vals[i].equals("null")){
                node.right = new TreeNode(Integer.parseInt(vals[i]));
                queue.add(node.right);
            }
            i++;
        }
        return root;
    }
}
```