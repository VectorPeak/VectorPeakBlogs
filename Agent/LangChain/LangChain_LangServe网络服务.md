# LangServe 网络服务

## 先给定位

LangServe 是把 LangChain Runnable 暴露成 HTTP 服务的工具。它解决的是“链路已经写好了，怎么给前端或其他系统调用”的问题

它像把本地函数包装成 API。函数内部仍然是 prompt、model、parser、retriever 或 agent，外部看到的是网络接口

## 适合什么场景

- 快速把 chain 暴露成 REST API
- 给前端、脚本或其他服务调用
- 为原型项目提供简单服务化入口
- 统一管理输入 schema 和输出 schema

典型思路是先构造一个 `Runnable`，再把它挂到 FastAPI 路由上

```python
from fastapi import FastAPI
from langserve import add_routes

app = FastAPI()
add_routes(app, chain, path="/chain")
```

## 和生产服务的边界

LangServe 能快速服务化，但生产环境仍然要补鉴权、限流、日志、错误码、超时、队列、灰度发布和监控告警

也就是说，LangServe 解决的是 LangChain 链路到 HTTP API 的桥接，不等于完整后端治理

## 对偶概念

LCEL 负责把组件组装成可运行对象，LangServe 负责把这个可运行对象变成可远程调用服务

## 参考

- https://python.langchain.com/docs/langserve/
