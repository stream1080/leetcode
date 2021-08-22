# 剑指Offer-32-从上到下打印二叉树I

## [题目链接](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-lcof/)

## 解析
这是一道对二叉树的层次遍历的题目

方法一：队列
- 定义一个队列，并将根节点入队列
- 如果队列不为空，出队，并加入list
- 如果出队元素左节点不为空，左节点入队
- 如果出队元素右节点不为空，右节点入队
- 将list转化成数组，输出结果



## 参考代码
```Java
class Solution {
    public int[] levelOrder(TreeNode root) {
        if(root == null) return new int[0];
        List<Integer> list = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<>();
        queue.add(root);//新建一个队列，让跟节点入队
        //如果队列不为空
        while(!queue.isEmpty()){
            //出队，并加入结果list中
            TreeNode node = queue.poll();
            list.add(node.val);
            //左右节点入队
            if(node.left != null) queue.add(node.left);
            if(node.right != null) queue.add(node.right);
        }
        //将list转化成数组返回，也可以用循环赋值
        return list.stream().mapToInt(Integer::valueOf).toArray();
    }
}
```