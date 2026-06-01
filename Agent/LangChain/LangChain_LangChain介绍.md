# LangChain 介绍

## 先给定位

LangChain 是大模型应用的工程编排框架，它不只是“调用 LLM 的 SDK”，而是把模型、提示词、输出解析、工具、检索、记忆和 Agent 运行时组织成可组合的应用链路

可以把它类比成后端里的 Web 框架：模型 API 像数据库驱动，单独能用，但真实应用还需要路由、状态、日志、错误处理、权限和部署方式

## 核心概念地图

- `Model`：连接 OpenAI、Anthropic、本地模型或 OpenAI 兼容接口
- `Prompt Template`：把变量、上下文和任务说明拼成稳定输入
- `Output Parser`：把模型输出转成 JSON、对象或业务字段
- `LCEL`：用管道式组合把多个 `Runnable` 串起来
- `Tool`：把搜索、数据库、业务 API 暴露给模型调用
- `Agent`：让模型在目标、工具和上下文之间循环决策
- `RAG`：先检索外部知识，再让模型基于证据生成答案
- `LangSmith`：追踪、调试和评测大模型链路

## 反向概念

LangChain 的反面不是“不用框架”，而是把所有逻辑写成零散脚本：一段拼 prompt，一段调模型，一段解析文本，一段查数据库，最后很难复用、观测和定位错误

数学上可以把一个应用链路看成函数复合：

$$
y = f_{parser}(f_{model}(f_{prompt}(x)))
$$

LangChain 做的是让这些函数有统一接口，并能继续扩展到工具调用、检索和状态管理

## 不知道自己不知道

学习 LangChain 时不要只背类名，要优先理解“输入稳定化”和“输出可控化”。LLM 的天然输出是概率文本，工程系统需要的是可复现、可追踪、可回滚的行为

## 参考

- https://docs.langchain.com/oss/python/langchain/overview
