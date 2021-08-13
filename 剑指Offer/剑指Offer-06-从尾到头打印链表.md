# 剑指 Offer 06. 从尾到头打印链表

## [题目链接](https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/)
输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

```
示例 1：
输入：head = [1,3,2]
输出：[2,3,1]
```

限制：
- 0 <= 链表长度 <= 10000



## 解析
- 先遍历一轮链表，计算链表的长度，用于新建数组
- 新建数组，用于结果返回
- 再一次从头到尾遍历链表，将节点从数组尾往数组头放置
- 返回数组




## 参考代码
```Java
class Solution {
    public int[] reversePrint(ListNode head) {
        ListNode dummy = head;
        int count = 0;
        //维护一个辅助节点，保存head
        //遍历链表，计算长度
        while(dummy != null){
            count++;
            dummy = dummy.next;
        }
        //定义结果数组
        int[] ans = new int[count];
        //将链表节点存入数组，从尾到头
        while(count>=0 && head !=null){
            ans[count-1] = head.val;
            count--;
            head = head.next;
        }
        //返回结果
        return ans;
    }
}
```