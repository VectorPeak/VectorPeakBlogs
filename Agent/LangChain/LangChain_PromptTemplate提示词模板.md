# PromptTemplate 提示词模板

## 先给定位

PromptTemplate 是把变量、上下文和任务说明组织成稳定提示词的组件。它解决的不是“写一句更玄的咒语”，而是把提示词从临时字符串变成可维护的输入协议

类比后端接口，prompt 就像请求体 schema。字段缺失、顺序混乱、约束模糊，模型输出就会更不稳定

## 它解决什么问题

- 把用户问题、背景资料、角色要求和输出格式分层组织
- 避免在代码里到处拼接字符串
- 让 prompt 可以复用、测试和版本管理
- 与 parser、model、retriever 形成稳定链路

典型写法：

```python
from langchain_core.prompts import ChatPromptTemplate

prompt = ChatPromptTemplate.from_messages([
    ("system", "你是一个严谨的技术导师"),
    ("user", "请解释这个概念：{topic}")
])
```

## 对偶概念

PromptTemplate 的对偶是 OutputParser。前者约束输入怎么进入模型，后者约束模型输出怎么回到程序

可以把一次 LLM 调用理解为：

$$
structured\_output = parser(model(prompt(variables)))
$$

只有 prompt 稳定，parser 才更容易稳定

## 常见误区

不要把所有业务规则都塞进一个超长 prompt。更稳的做法是把规则拆成系统提示、上下文、示例、约束和输出 schema，并把动态资料通过变量传入

## 参考

- https://python.langchain.com/api_reference/core/prompts.html
