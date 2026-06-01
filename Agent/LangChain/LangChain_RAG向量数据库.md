# RAG 向量数据库

## 先给定位

向量数据库负责存储 embedding，并根据语义相似度召回相关片段。它是 RAG 的召回层，不是答案生成层

可以把 embedding 理解为把文本投影到高维空间。语义接近的文本，在向量空间中距离也更近

## 基本原理

文本向量化后，每个 chunk 都变成一个向量：

$$
v_i = E(d_i)
$$

查询也会被向量化：

$$
v_q = E(q)
$$

检索时通常计算余弦相似度：

$$
cos(\theta)=\frac{v_q \cdot v_i}{\|v_q\|\|v_i\|}
$$

相似度越高，说明两个向量方向越接近

## 选型维度

- 数据规模和写入频率
- 查询延迟和并发
- metadata filter 能力
- 混合检索能力
- 权限隔离和多租户
- 备份恢复和运维成本

常见选择包括 FAISS、Chroma、Qdrant、Milvus、Weaviate、Pinecone 以及云厂商向量检索服务

## 不要只靠向量检索

向量检索擅长语义相似，但不一定擅长精确编号、专有名词、代码符号和日期过滤。工程里通常会结合 BM25、关键词检索、metadata filter 和 reranker

## 参考

- https://docs.langchain.com/oss/python/integrations/vectorstores
- https://python.langchain.com/docs/concepts/vectorstores/
