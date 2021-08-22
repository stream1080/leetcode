# 剑指Offer-25-合并两个排序的链表

## [题目链接](https://leetcode-cn.com/problems/he-bing-liang-ge-pai-xu-de-lian-biao-lcof/)

## 解析

方法一：归并排序
- 由于两个链表都是有序的，可以使用归并排序进行合并
- 新建一个链表头，遍历两个链表
- 两两比较节点，将小的节点接到新的链表上
- 当其中一个链表结束后，将另一个链表剩余部分接到新链表上，返回

## 参考代码
```Java
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        //新建一个链表
        ListNode dummy = new ListNode(0);
        ListNode head = dummy;
        while(l1!=null && l2!=null){
            //两两比较，将小的接到新链表上
            if(l1.val<l2.val){
                head.next = l1;
                l1 = l1.next;
            }else{
                head.next = l2;
                l2 = l2.next;
            }
            head = head.next;
        }
        //将剩余部分接到新链表上
        head.next = l1==null?l2:l1;
        return dummy.next;
    }
}
```