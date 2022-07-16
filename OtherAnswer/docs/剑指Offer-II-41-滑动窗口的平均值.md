# 剑指Offer-II-41-滑动窗口的平均值

- [题目链接](https://leetcode.cn/problems/qIsx9U/)

## 解析

方法一：队列
- 将元素存入队列，并且累加
- 如果元素个数达到 size，则队头出队
- 并且 sum 减去这个元素
- 返回 sum / 队列大小


## 参考代码
```Java
方法一：
class MovingAverage {
    Queue<Integer> queue;
    double sum;
    int size;

    /** Initialize your data structure here. */
    public MovingAverage(int size) {
        queue = new ArrayDeque<>();
        this.sum = 0;
        this.size = size;
    }
    
    public double next(int val) {
        if(queue.size() == size)
            sum -= queue.poll();
        queue.offer(val);
        sum += val;
        return sum / queue.size();
    }
}
```
