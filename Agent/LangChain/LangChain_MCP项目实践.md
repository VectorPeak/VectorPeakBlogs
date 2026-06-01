# MCP 项目实践

## 先给定位

MCP 是 Model Context Protocol，用来把外部工具、资源和上下文以标准方式暴露给大模型应用。它的价值是降低工具接入的重复成本

如果 Tool 是单个插座，MCP 更像统一电源面板。应用不需要为每个工具都写一套私有接入协议

## MCP 适合解决什么

- 让 Agent 访问文件、数据库、浏览器、搜索或内部系统
- 把工具能力从应用代码里拆出来独立维护
- 让不同客户端复用同一个工具服务器
- 用统一协议描述工具、资源和调用结果

在 LangChain 项目中，MCP 通常出现在 Agent 工具接入层：Agent 通过适配器连接 MCP server，再把 server 暴露的能力变成可调用工具

## 项目实践顺序

1. 先明确 Agent 需要哪些外部能力
2. 把能力拆成只读、写入和高风险操作
3. 为每个工具设计明确输入 schema
4. 在 MCP server 中实现工具
5. 在 LangChain 侧加载工具并接入 Agent
6. 加入权限、日志、超时和错误提示

## 常见误区

不要为了“用了 MCP”而把所有函数都包成 MCP。只有当工具需要跨客户端复用、独立部署、权限隔离或标准化发现时，MCP 才明显有价值

## 参考

- https://docs.langchain.com/oss/python/integrations/tools/mcp
- https://modelcontextprotocol.io/docs
