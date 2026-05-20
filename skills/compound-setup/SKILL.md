---
name: compound-setup
description: "系统初始化。加载所有compound核心skill，建立项目执行上下文。新环境或新session进入时执行一次。"
source: compound
---

# compound-setup

## 用途
一步加载所有核心 skill，建立项目结构规范。

## 加载清单

依次安装以下 skill：

```yaml
project-startup: 新项目启动流程
evaluator: 评估器（持怀疑态度）
analogy: 比喻（用户理解桥梁）
translator: 翻译（需求→文档）
planner: 规划（分步task）
agent-interaction: 智能体交互
feishu-doc-ingest: 飞书文档摄取
lark-shared: 飞书认证配置
```

## 初始化后

Agent 就绪，可执行任何项目。没有 startup.md 时，用 project-startup skill 走通用流程。
