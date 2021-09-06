# 剑指Offer-59-队列的最大值II

## [题目链接](https://leetcode-cn.com/problems/dui-lie-de-zui-da-zhi-lcof/)

## 解析
方法一：辅助队列
- 用一个队列作为辅助，主要队列中的最大值

## 参考代码
```Java
class MaxQueue {
    private Deque<Integer> queue;
    private Deque<Integer> help;

    // 构造函数
    public MaxQueue() {
        queue = new ArrayDeque<>();
        help  = new ArrayDeque<>(); 
    }
    
    // 从辅助队列中取最大值
    public int max_value() {
        return queue.isEmpty()?-1:help.peek();
    }
    
    // 入队，更新辅助队列的最大值
    public void push_back(int value) {
        queue.offer(value);
        while(!help.isEmpty() && value > help.peekLast()){
            help.pollLast();
        }
        help.offer(value);
    }
    
    // 出队，如果队头为出队元素，辅助队出队
    public int pop_front() {
        if(queue.isEmpty()) return -1;
        int val = queue.pop();
        if(help.peek() == val){
            help.pop();
        }
        return val;
    }
}

```