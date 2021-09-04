# 剑指Offer-31-栈的压入、弹出序列

## [题目链接](https://leetcode-cn.com/problems/zhan-de-ya-ru-dan-chu-xu-lie-lcof/)

## 解析

方法一：模拟
- 定义一个栈，将pushed元素依次入栈
- 当栈顶元素与popped元素相等时，出栈
- 遍历结束后，判断栈是否为空

## 参考代码
```Java
class Solution {
    public boolean validateStackSequences(int[] pushed, int[] popped) {
        Deque<Integer> stack = new ArrayDeque();
        for(int i=0,j=0;i<pushed.length;i++){
            stack.push(pushed[i]);
            while(!stack.isEmpty() && stack.peek() == popped[j]){
                stack.pop();
                j++;
            }
        }
        return stack.isEmpty();
    }
}
```