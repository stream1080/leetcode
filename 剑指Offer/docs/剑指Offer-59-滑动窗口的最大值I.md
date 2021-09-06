# 剑指Offer-59-滑动窗口的最大值I

## [题目链接](https://leetcode-cn.com/problems/hua-dong-chuang-kou-de-zui-da-zhi-lcof/)

## 解析
方法一：单调队列
- 定义一个队列，遍历数组
- 将数组元素入队，进入下一轮循环
- 如果当前元素大于队尾元素，则队尾循环出队，保证队尾元素为最大值
- 如果窗口元素个数大于k，队头出队，滑动窗口

## 参考代码
```Java
class Solution {
    public int[] maxSlidingWindow(int[] nums, int k) {
        if(nums.length == 0 || k == 0) return new int[0];
        Deque<Integer> deque = new LinkedList<>();
        int[] res = new int[nums.length - k + 1];
        for(int j = 0, i = 1 - k; j < nums.length; i++, j++) {
            // 删除队列中对应的 nums[i-1]，滑动窗口
            if(i > 0 && deque.peekFirst() == nums[i - 1])
                deque.removeFirst();
            // 保持队列递减，保证队头为最大值
            while(!deque.isEmpty() && deque.peekLast() < nums[j])
                deque.removeLast();
            // 元素入队
            deque.addLast(nums[j]);
            // 记录窗口最大值
            if(i >= 0)
                res[i] = deque.peekFirst();
        }
        return res;
    }
}

```