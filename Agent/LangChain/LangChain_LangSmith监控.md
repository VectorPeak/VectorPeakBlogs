# LangSmith 监控

## 先给定位

LangSmith 是 LangChain 生态里的观测、调试和评测平台。它解决的是大模型链路“看不见中间过程”的问题

普通后端有日志、链路追踪和指标，大模型应用也需要看到 prompt、模型响应、工具调用、检索结果、token 成本和错误栈

## 它能看什么

- 每次调用的输入和输出
- prompt 渲染后的真实内容
- 模型延迟、token 和成本
- tool 调用参数和返回结果
- RAG 检索到的文档片段
- Agent 每一轮决策轨迹
- 评测数据集和打分结果

## 为什么重要

没有观测时，模型答错很难定位原因。可能是 prompt 不清楚，可能是检索没命中，可能是工具返回错，可能是 parser 失败，也可能是模型能力不够

LangSmith 的价值就是把一次黑盒调用拆成可复盘链路

## 相关概念

- `Tracing`：记录一次运行的调用树
- `Dataset`：保存测试输入和期望输出
- `Evaluation`：对模型或链路做自动评测
- `Experiment`：比较不同 prompt、模型或检索策略的效果

## 参考

- https://docs.smith.langchain.com/
- https://docs.smith.langchain.com/observability
- https://docs.smith.langchain.com/evaluation
