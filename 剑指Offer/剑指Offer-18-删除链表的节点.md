# 剑指Offer-18-删除链表的节点

## [题目链接](https://leetcode-cn.com/problems/shan-chu-lian-biao-de-jie-dian-lcof/)

## 解析
本题可以使用双指针，用一个指针保存上一个节点，遍历到val后，删除当前即可
我们这次不需要双指针，由于两个指针是相邻的，之间用next即可

方法一：双指针
- 定义一个哨兵，避免一些边界条件
- 如果p.next.val == val , p.next = p.next.next;
- 返回结果


## 参考代码
```Java
class Solution {
    public ListNode deleteNode(ListNode head, int val) {
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode p = dummy;
        while(p.next!=null){
            if(p.next.val == val){
                //删除节点，之间返回
                p.next = p.next.next;
                return dummy.next;
            }  
            p = p.next;
        }
        return dummy.next;
    }
}
```