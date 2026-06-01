# Agent 智能体

## 先给定位

Agent 是由大模型驱动的决策循环。它不是一次模型调用，而是在目标、上下文、工具和中间结果之间反复判断下一步动作的执行系统

Chain 像固定流水线，Agent 像带调度能力的操作员。前者按预设步骤走，后者根据观察结果决定是否继续调用工具或直接回答

## 基本循环

一个 Agent 通常会反复执行：

1. 读取当前消息和状态
2. 判断是否需要工具
3. 生成工具调用参数
4. 执行工具并观察结果
5. 决定继续调用、补充检索或输出最终答案

LangChain 1.x 中，官方推荐用 `create_agent` 创建 Agent，底层运行在 LangGraph Runtime 上

```python
from langchain.agents import create_agent

agent = create_agent(
    model=model,
    tools=[search_tool],
    system_prompt="你是一个严谨的研究助手"
)
```

## 真正难点

Agent 的难点不在“能不能调用工具”，而在循环控制、权限边界、状态持久化、错误恢复、成本限制和可观测性

一个没有预算限制的 Agent 可能一直检索，一个没有权限边界的 Agent 可能调用危险工具，一个没有日志的 Agent 很难复盘错误来自模型、工具还是上下文

## 参考

- https://docs.langchain.com/oss/python/langchain/agents
