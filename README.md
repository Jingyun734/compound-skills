# Compound Skills

自定义 AI Agent skills 合集，覆盖项目启动、文档摄取、评估推理等核心工作流。

## 安装

```bash
# 一键安装全部 skills
npx skills add Jingyun734/compound-skills -y -g
```

或按需安装单个 skill：

```bash
install_skill(github_url="https://github.com/Jingyun734/compound-skills/blob/main/skills/compound-setup/SKILL.md", user_requested=true)
```

## Skills

| Skill | 用途 |
|-------|------|
| compound-setup | 系统初始化：一步加载所有核心 skill |
| project-startup | 新项目启动流程 |
| evaluator | 评估器：质疑+结构化反馈 |
| analogy | 比喻：将抽象语言转化为用户可理解的描述 |
| translator | 翻译：用项目语言将需求转化为需求文档 |
| planner | 规划：拆解需求为可执行 task 方案 |
| agent-interaction | 智能体交互：多代理协调与质量保障 |
| feishu-doc-ingest | 飞书文档摄取→Markdown raw |
