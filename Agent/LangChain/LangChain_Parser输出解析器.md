# Parser 输出解析器

## 先给定位

Parser 是把模型输出从自然语言文本转成程序可消费结构的组件。它的核心价值是让 LLM 的输出进入后续业务流程，而不是只停留在一段看似正确的文字

如果 PromptTemplate 是输入协议，Parser 就是输出协议。一个管输入，一个管输出

## 为什么需要 Parser

LLM 默认输出是文本，但业务系统常常需要字段、标签、JSON、列表、评分或可执行参数。没有解析器，就只能靠正则和人工约定硬拆文本

常见目标包括：

- 提取结构化字段
- 校验 JSON 格式
- 生成分类标签
- 把回答拆成步骤、证据和结论
- 与工具调用或数据库写入对接

## 相关概念

- `StrOutputParser`：把模型消息转成字符串
- `JsonOutputParser`：解析 JSON 结构
- `PydanticOutputParser`：用类型模型约束字段
- `structured output`：让模型直接按 schema 返回结构化结果

## 工程边界

Parser 不能保证模型永远正确，它只是提高输出可控性。生产场景还需要重试、schema 校验、异常分支和兜底策略

形式上可以把解析看成从文本空间到结构空间的映射：

$$
g: T \rightarrow S
$$

其中 `T` 是自然语言文本集合，`S` 是业务结构集合。解析失败说明模型输出没有落在可解析区域内

## 参考

- https://python.langchain.com/api_reference/core/output_parsers.html
