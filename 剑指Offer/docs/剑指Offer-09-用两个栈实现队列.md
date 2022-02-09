# 剑指 Offer 09. 用两个栈实现队列

## [题目链接](https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/)
用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 appendTail 和 deleteHead ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，deleteHead 操作返回 -1 )

```
示例 1：
输入：
["CQueue","appendTail","deleteHead","deleteHead"]
[[],[3],[],[]]
输出：[null,null,3,-1]

示例 2：
输入：
["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
[[],[],[5],[2],[],[]]
输出：[null,-1,null,null,5,2]
```
提示：

- 1 <= values <= 10000
- 最多会对 appendTail、deleteHead 进行 10000 次调用


## 解析
#### 读题
- 先解释一下题目，题目要求用两个栈实现一个先进先出的队列，
- 示例数据中，第一行是执行的方法，第二行是方法的参数，第三行是输出

#### 思路
- 入队时，将元素进入栈1
- 出队时，先判断栈2中是否有元素，
- 如果栈2为空，则将栈1的元素一一进入栈2
- 如果栈1也为空，则为空队，返回-1
- 否则返回栈2顶元素


## 参考代码
```Java
class CQueue {
    //定义两个栈
    private Stack<Integer> stack1;
    private Stack<Integer> stack2;

    //初始化两个栈
    public CQueue() {
        this.stack1 = new Stack<Integer>();
        this.stack2 = new Stack<Integer>();
    }
    
    // 入队统一进入栈1
    public void appendTail(int value) {
        stack1.push(value);
    }
    
    //出队
    public int deleteHead() {
        //如果栈2为空，则将栈1的数据一一进入栈2
        if(stack2.isEmpty()){
            while(!stack1.isEmpty()){
                stack2.push(stack1.pop());
            }
        }
        //如果栈2为空，则为空队，返回-1
        if(stack2.isEmpty())
            return -1;
        else
            return stack2.pop(); //否则返回栈顶元素
    }
}

/**
 * Your CQueue object will be instantiated and called as such:
 * CQueue obj = new CQueue();
 * obj.appendTail(value);
 * int param_2 = obj.deleteHead();
 */
```