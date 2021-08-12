# 剑指 Offer 24. 反转链表

## [题目链接](https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/)
定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点。

```
示例:
输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL
```

限制：
- 0 <= 节点个数 <= 5000

 

[相同题目](https://leetcode-cn.com/problems/reverse-linked-list/)




## 解析
- 定义两个节点，用于保存当前节点的前置节点和后置节点
- 将当前节点指向前一个节点，反转
- 下一步，pre往后，head往后




## 参考代码
```Java
class Solution {
    public ListNode reverseList(ListNode head) {
        //定义两个节点作为辅助节点
        ListNode pre = null,next = null;
        //遍历链表
        while(head != null){
            next = head.next;//保存后置节点
            head.next = pre;//反转
            pre = head; //pre往后一步
            head = next; //head 往后一步
        }
        //返回反转后的头节点
        return pre;
    }
}
```