# 剑指Offer-22-链表中倒数第k个节点

## [题目链接](https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/)

## 解析
方法一：快慢双指针
- 定义快慢两个指针，快指针先走k步
- 快慢指针同时走，快指针到头时，慢指针为倒是第k个节点
- 返回结果


## 参考代码
```Java
class Solution {
    public ListNode getKthFromEnd(ListNode head, int k) {
        ListNode left = head,rigth = head;
        //快指针先走k步
        while(rigth!=null && k>0){
            k--;
            rigth = rigth.next;
        }
        //快慢指针同时走，快指针到头时，慢指针为倒是第k个节点
        while(rigth!=null){
            left = left.next;
            rigth = rigth.next;
        }
        //返回结果
        return left;
    }
}
```