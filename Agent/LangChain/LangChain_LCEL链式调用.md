# LCEL 链式调用

## 先给定位

LCEL 是 LangChain Expression Language，用来把 prompt、model、parser、retriever、tool 等组件组合成可运行链路

它像 Unix 管道：前一个组件的输出变成后一个组件的输入，复杂流程由小组件组合出来

## 基本形态

最常见的链式写法是：

```python
chain = prompt | model | parser
result = chain.invoke({"topic": "RAG"})
```

这里的 `|` 不是装饰语法，而是把多个 `Runnable` 组合成一个新的 `Runnable`

## LCEL 带来的能力

- 统一 `invoke`、`batch`、`stream` 等调用方式
- 让链路可以拆分、复用和测试
- 支持并行、分支、映射和回退
- 更容易接入 LangSmith 做链路追踪

## 和普通函数调用的区别

普通函数调用当然也能完成同样逻辑，但 LCEL 的优势是让每个节点都遵守统一协议。统一协议带来的不是语法好看，而是批处理、流式输出、观测和组合能力

数学上它就是函数复合：

$$
(h \circ g \circ f)(x) = h(g(f(x)))
$$

LCEL 把这个思想落到了大模型应用的工程组件上

## 参考

- https://python.langchain.com/docs/concepts/lcel/
