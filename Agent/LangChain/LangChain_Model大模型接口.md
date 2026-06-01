# Model 大模型接口

## 先给定位

Model 接口是 LangChain 连接大语言模型的适配层。业务代码不应该直接散落在各个厂商的 HTTP API 上，而应该通过统一对象调用模型

它像数据库里的 ORM 或驱动层：底层可以换 MySQL、PostgreSQL 或 SQLite，上层代码仍然尽量保持同一种访问方式

## 为什么要有模型接口

不同模型供应商在鉴权、消息格式、流式返回、工具调用、结构化输出和错误码上都有差异。Model 接口的作用是把这些差异收敛到一个统一调用面

常见调用形态包括：

```python
from langchain_openai import ChatOpenAI

model = ChatOpenAI(model="gpt-4.1-mini", temperature=0)
response = model.invoke("用一句话解释 LangChain")
```

这里的 `model` 可以继续接到 prompt、parser、tool 或 agent 里，而不是只作为一次性 API 调用

## 相关概念

- `ChatModel`：面向多轮消息的聊天模型接口
- `LLM`：更传统的纯文本输入输出接口
- `Embedding`：把文本映射为向量，常用于 RAG 检索
- `Provider package`：例如 `langchain-openai`、`langchain-anthropic`

## 选型要看什么

模型选型不能只看榜单，还要看工具调用、结构化输出、上下文长度、延迟、成本、合规、可用区和降级策略

如果要写成数学形式，可以把模型看成条件概率分布：

$$
P(y \mid x, c, \theta)
$$

其中 `x` 是用户输入，`c` 是上下文，`\theta` 是模型参数。工程里能控制的主要是输入、上下文、模型选择和调用参数

## 参考

- https://docs.langchain.com/oss/python/langchain/models
