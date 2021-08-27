# 剑指Offer-41-数据流中的中位数

## [题目链接](https://leetcode-cn.com/problems/find-median-from-data-stream/submissions/)

## 解析
方法一：最大堆+最小堆
- 使用最大堆和最小堆存储元素
- 当m=n：则中位数为(A的堆顶元素+B的堆顶元素)/2。
- 当m != n：则中位数为A的堆顶元素。


## 参考代码
```Java
class MedianFinder {

    PriorityQueue<Integer> queMin; //存储比较小的那一半的值
    PriorityQueue<Integer> queMax; //存储比较大的那一半的值

    /** initialize your data structure here. */
    public MedianFinder() {
        queMax = new PriorityQueue<>((a,b)->(a-b));
        queMin = new PriorityQueue<>((a,b)->(b-a));
    }
    
    public void addNum(int num) {
        if(queMin.isEmpty() || num<=queMin.peek()){
            queMin.offer(num);
            if(queMax.size() + 1 < queMin.size()){
                queMax.offer(queMin.poll());
            }
        }else{
            queMax.offer(num);
            if(queMax.size() > queMin.size()){
                queMin.offer(queMax.poll());
            }
        }
    }
    
    public double findMedian() {
        if(queMin.size() > queMax.size())
            return queMin.peek();
        return (queMin.peek() + queMax.peek()) / 2.0;
    }
}

```