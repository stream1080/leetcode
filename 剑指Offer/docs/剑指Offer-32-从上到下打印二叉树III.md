# 剑指Offer-32-从上到下打印二叉树III

## [题目链接](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/submissions/)

## 解析
这次是按照Z子层次遍历，简单来说就是，奇数层从左到右，偶数层从右到左

方法一：双端队列
- 定义一个队列，如果根节点不为空，则入队，否则返回空
- 如果队列不为空，进入循环，建立一个临时双端队列
- 此时队列中元素为当前层的元素，
- 进入循环，注意，由于循环内有出入队操作，所以循环条件先定义i=queue.size()
- 出队，判断list.size()的奇偶数，奇数层，添加到队列头部。偶数层，添加到队列尾部
- 如果出队元素左节点不为空，左节点入队
- 如果出队元素右节点不为空，右节点入队
- 当前层遍历结束，将临时队列加入结果List
- 遍历结束，返回结果



## 参考代码
```Java
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        List<List<Integer>> list = new ArrayList<>();
        if(root != null) queue.add(root);
        while(!queue.isEmpty()){
            //新建一个双端队列
            LinkedList<Integer> tmp = new LinkedList<>();
            for(int i=queue.size();i>0;i--){
                TreeNode node = queue.poll();
                //偶数层，添加到队列尾部
                if(list.size()%2==0)
                    tmp.addLast(node.val);
                //奇数层，添加到队列头部
                else 
                    tmp.addFirst(node.val);
                if(node.left != null) queue.add(node.left);
                if(node.right != null) queue.add(node.right);
            }
            list.add(tmp);
        }
        return list;
    }
}
```