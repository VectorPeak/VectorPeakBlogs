# 项目框架

这个文件用于说明仓库的目录和关键文件分工。根目录 `AGENTS.md` 只保留最短协作规则，项目结构说明放在这里。

## 根目录结构

- `Agent/`：Agent 相关内容，现代 Agent 文章统一放在 `Agent/Modern_Agent/`
- `ai-tools/`：AI 工具相关页面
- `DeepLearning/`：深度学习学习记录和专题内容
- `essentials/`：基础指南和核心说明页面
- `images/`：站点图片资源，LeetCode 图示优先放在 `images/leetcode/`
- `LeetCode/`：算法学习、题解和数据结构内容
- `snippets/`：可复用代码片段或 Mintlify snippets
- `agents_md_hub/`：协作指令的详细说明文件

## 根目录关键文件

- `AGENTS.md`：协作规则入口，保持短小，控制在 200 行以内
- `docs.json`：Mintlify 站点主配置，导航和站点结构以它为准
- `index.mdx`：站点首页
- `quickstart.mdx`：快速开始页面
- `development.mdx`：开发相关页面
- `README.md`：仓库基础说明
- `LICENSE`：许可证文件
- `.mintignore`：Mintlify 构建忽略规则

## agents_md_hub 文件

- `project_framework.md`：项目结构、目录职责和关键文件说明
- `project_instruction.md`：写作风格、内容边界、图示规范和仓库具体协作约定

## 修改原则

- 改导航时同步检查 `docs.json` 和对应 `MDX` 文件
- 改目录或文件名时同步检查页面内链接
- 新增内容前先判断它属于现有哪个栏目
- 不确定归属时，优先保持现有栏目结构，不随意新增顶层目录
