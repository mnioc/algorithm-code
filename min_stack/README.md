# 包含min函数的栈

## 要求

定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

## 样例

```shell
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.min();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.min();   --> 返回 -2.
```

## 思路    

用两个栈去实现这个要求，

- 栈a存储原始出入栈的数据
- 栈b存储最小值，需要保持栈b是一个从栈底到栈顶降序的顺序（不需要存储栈a的所有元素）

辅助栈栈b的设计理念：每一个入栈a的元素，都跟栈b的栈顶元素进行比较，只要比栈b的栈顶元素小或者等于栈b元素，就压入栈b
否则，就不压（这里是因为假如进来的元素比当前最小的大，我们可以不用理会它，是因为这个大元素压住了我们原始的小元素，只有当这个
大元素弹出去的时候，我们的小元素才能被弹出，所按照这样的模式，栈b的栈顶元素永远都会是最小的）