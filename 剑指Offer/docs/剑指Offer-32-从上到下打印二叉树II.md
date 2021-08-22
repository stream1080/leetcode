# 剑指Offer-32-从上到下打印二叉树II

## [题目链接](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-ii-lcof/)

## 解析
这是一道对二叉树的层次遍历的题目，按层遍历

方法一：按层遍历
- 定义一个队列，如果根节点不为空，则入队，否则返回空
- 如果队列不为空，进入循环，建立一个临时List
- 此时队列中元素为当前层的元素，
- 进入循环，出队，加入临时List。注意，由于循环内有出入队操作，所以循环条件先定义i=queue.size()
- 如果出队元素左节点不为空，左节点入队
- 如果出队元素右节点不为空，右节点入队
- 当前层遍历结束，将临时list加入结果List
- 遍历结束，返回结果



## 参考代码
```Java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        List<List<Integer>> list = new ArrayList<>();
        Queue<TreeNode> queue = new LinkedList<>();
        //如果根节点不为空，则入队，否则返回空
        if(root !=null ) queue.add(root);
        while(!queue.isEmpty()){
            //建立一个临时List
            List<Integer> tmp = new ArrayList<>();
            //按层打印，由于循环内有出入队操作，所以循环条件先定义i=queue.size()
            for(int i=queue.size();i>0;i--){
                TreeNode node = queue.poll();
                tmp.add(node.val);
                if(node.left != null) queue.add(node.left);
                if(node.right != null) queue.add(node.right);
            }
            //将当前层加入结果中
            list.add(tmp);
        }
        return list;
    }
}
```