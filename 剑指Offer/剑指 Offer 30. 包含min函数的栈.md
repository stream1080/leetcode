# 剑指 Offer 30. 包含min函数的栈

## [题目链接](https://leetcode-cn.com/problems/bao-han-minhan-shu-de-zhan-lcof/)
定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

 
```
示例:
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.min();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.min();   --> 返回 -2.
```

提示：
- 各函数的调用总次数不超过 20000 次

[相同题目：leetcode-115](https://leetcode-cn.com/problems/min-stack/)


## 解析
难点：将 min() 函数复杂度降为 O(1)O(1) ，可通过建立辅助栈实现
- 栈1 ： 栈1用于存储所有元素，保证入栈 push() 函数、出栈 pop() 函数、获取栈顶 top() 函数的正常逻辑。
- 栈2 ： 栈2中存储栈1所有 非严格降序 的元素，则栈1中的最小元素始终对应栈2的栈顶元素，即 min() 函数只需返回栈2的栈顶元素即可。




## 参考代码
```Java
class MinStack {
    //定义两个栈，一个主栈，另一个辅助实现min()函数
    private Stack<Integer> stack1;
    private Stack<Integer> stack2;

    /** initialize your data structure here. */
    public MinStack() {
        stack1 = new Stack<>();
        stack2 = new Stack<>();
    }
    
    public void push(int x) {
        stack1.push(x);
        //如果栈2为空，或者栈2顶元素大于x，则x入栈为栈顶
        if(stack2.isEmpty() || stack2.peek()>x)
            stack2.push(x);
        else
            stack2.push(stack2.peek());//否则，保持原有的最小值
    }
    //出栈时，两个栈同时出栈
    public void pop() {
        stack1.pop();
        stack2.pop();
    }
    //获取主栈栈顶元素
    public int top() {
        return stack1.peek();
    }
    //获取辅助栈最小元素，在栈顶则为最小
    public int min() {
        return stack2.peek();
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.min();
 */
```