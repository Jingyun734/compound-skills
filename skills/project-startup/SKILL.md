---
name: project-startup
description: "新项目启动流程。当用户说启动新项目、开始做xx、立项时触发。加载此skill后，按通用流程执行，逐步收敛为具体项目配置。"
source: compound
---

# Project Startup

## 触发条件

用户说"启动新项目""开始做XX""立项""我想做XX"时加载此skill。

## 项目结构规则

```
projects/<项目名>/
├── startup.md     ← 启动配置（Agent 读取后执行）
└── log/           ← 运行记录（Agent 每次执行后追加）
```

除 startup.md 和 log/ 外，项目目录不放任何文件。

## startup.md 格式

```yaml
project: <名称>
scope: <边界>

prerequisites:
  - <条件1>
  - <条件2>

steps:
  - <步骤1>
  - <步骤2>

trigger:
  - <可能触发的其他项目>
```

## 执行流程

1. 加载评估器skill、比喻skill、翻译skill、规划skill、智能体交互skill
2. 创建评估器智能体，通过交互skill保证执行质量
3. 检索knowledge、GitHub或相关官方文档，消化出所需skill
4. 根据已有raw文件或外部信息，设计顶层项目语言
5. 评估器评估语言逻辑性并质疑
6. 触发比喻skill，向用户描述项目，获取用户需求
7. 触发翻译skill，用项目语言把需求翻译成需求文档
8. 评估器评估翻译准确性
9. 通过后触发规划skill，给出分步task方案
10. 执行完毕后评估器评估产物与需求一致性
11. 不通过→重新规划；通过→用户评估
12. 用户不通过→指出不足返回；通过→结项

## 收尾

写日志，触发消化skill总结项目经验，检查是否需要触发其他项目。

## 日志格式

`log/` 文件命名 `YYYY-MM-DD-N.md`。三要素：做了什么、为什么、结果。

## 新项目启动流程

① 查 knowledge/system/ 和 knowledge/raw/ 获取设计参考
② 搜索 GitHub 或相关文档获取外部规范
③ 撰写 startup.md
④ 确认 prerequisites 满足
⑤ 执行
⑥ 写日志
