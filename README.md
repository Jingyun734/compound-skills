# Compound Skills

自定义 AI Agent skills 合集，覆盖项目启动、文档摄取、评估推理等核心工作流。

## 安装

```bash
npx skills add Jingyun734/compound-skills -y -g
```

## 分类

### 自定义核心

项目启动、文档摄取、评估、规划、智能体交互等核心工作流。

| Skill | 用途 |
|-------|------|
| compound-setup | 系统初始化：一步加载所有核心 skill |
| project-startup | 新项目启动流程 |
| feishu-doc-ingest | 飞书文档摄取→Markdown raw |
| compound-inspection | 文件系统巡检 |
| evaluator | 评估器：质疑+结构化反馈 |
| analogy | 比喻：用户理解桥梁 |
| translator | 翻译：需求→文档 |
| planner | 规划：分步 task 方案 |
| agent-interaction | 智能体交互：多代理协调 |

### 历史 compound skill

旧版 compound 系统遗留 skill，按需安装。

| Skill | 用途 |
|-------|------|
| compound-ingestion-conversation | 对话摄取 |
| compound-digestion-extract-concepts | 概念提取消化 |
| compound-digestion-map-concepts | 概念映射消化 |
| compound-digestion-summary | 摘要消化 |
| compound-digestion-update-index | 索引更新消化 |
| compound-output-knowledge | 知识层输出 |
| compound-output-project | 项目层输出 |
| compound-output-review | 复盘输出 |
| compound-project-closure | 项目结项 |
| compound-project-startup | 项目启动（历史版本） |

### 系统 skill

Hanako 系统自带 skill，按需安装。

| Skill | 用途 |
|-------|------|
| companion-v2 | 认知伙伴 |
| file-butler | 文件管理 |
| manual-creator | 手动创建 |
| plan-intake-protocol | 计划摄入协议 |
| system-migration | 系统迁移 |
