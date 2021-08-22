# 剑指Offer-52-两个链表的第一个公共节点

## [题目链接](https://leetcode-cn.com/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/)

## 解析

方法一：遍历
- 遍历数组，条件为p1!=p2
- p1到尾部时，让他从p2开始遍历
- p2到尾部时，让他从p1开始遍历
- 这样p1和p2走的路径一样
- 如果链表相交，一定会相遇


## 参考代码
```Java
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode p1 = headA,p2 = headB;
        while(p1 != p2){
           p1 = p1 == null?headB:p1.next;
           p2 = p2 == null?headA:p2.next;
        }
        return p1;
    }
}
```