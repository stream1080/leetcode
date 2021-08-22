# 剑指 Offer 35. 复杂链表的复制

## [题目链接](https://leetcode-cn.com/problems/fu-za-lian-biao-de-fu-zhi-lcof/)
请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null。

 
```
示例 1：
输入：head = [[7,null],[13,0],[11,4],[10,2],[1,0]]
输出：[[7,null],[13,0],[11,4],[10,2],[1,0]]

示例 2：
输入：head = [[1,1],[2,1]]
输出：[[1,1],[2,1]]

示例 3：
输入：head = [[3,null],[3,0],[3,null]]
输出：[[3,null],[3,0],[3,null]]

示例 4：
输入：head = []
输出：[]
解释：给定的链表为空（空指针），因此返回 null。
```

提示：

- -10000 <= Node.val <= 10000
- Node.random 为空（null）或指向链表中的节点。
- 节点数目不超过 1000 。
 

[相同题目](https://leetcode-cn.com/problems/copy-list-with-random-pointer/)



## 方法一：哈希表
题目看起来比较难以理解，简单来说就是复制一个新的链表
这个链表是特殊链表，处理next，还存在一个random随机节点

- 新建一个Map，新旧节点一一对应，
- 将新节点的next和random赋值
- 返回新链表的头节点



## 参考代码
```Java
class Solution {
    public Node copyRandomList(Node head) {
        if(head == null)
            return head;
        Map<Node,Node> map = new HashMap<>();
        //将Map中新节点和旧节点一一对应
        for(Node cur=head;cur != null;cur = cur.next){
            map.put(cur,new Node(cur.val));
        }
        //将新节点的next和random赋值
        for(Node cur=head;cur != null;cur = cur.next){
            map.get(cur).next = map.get(cur.next);
            map.get(cur).random = map.get(cur.random);
        }
        //返回新链表
        return map.get(head);
    }
}
```

## 方法二：原地修改-迭代
- 在每一个节点的后面复制一个节点
- 1-2-3变成1-1'-2-2'-3-3'
- 将复制后的节点的random赋值
- 分离新链表和原链表
- 返回结果

## 参考代码
```Java
class Solution {
    public Node copyRandomList(Node head) {
        if(head == null)
            return head;
        //在每一个节点后面复制一个新节点
        for(Node node = head,copy = null;node != null;node = node.next.next){
            copy = new Node(node.val);
            copy.next = node.next;
            node.next = copy;
        }
        //将每个节点的random进行赋值
        for(Node node = head;node != null;node = node.next.next){
            if(node.random != null){
                node.next.random = node.random.next;
            }
        }
        //分离链表
        Node newHead = head.next;
        for(Node node = head,temp = null;node != null && node.next != null;){
            temp = node.next;
            node.next = temp.next;
            node = temp;
        }
        //返回
        return newHead;
    }
}
```

