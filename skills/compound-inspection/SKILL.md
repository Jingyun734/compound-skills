---
name: compound-inspection
description: "Compound 文件系统巡检。当用户说巡检、检查系统、看看有没有问题时触发。扫描全部文件，检查格式一致性、孤引用、未落地项。做了大量文件修改后主动提醒用户可以巡检。"
source: compound
---

# Compound 文件系统巡检

## 执行

扫描所有非 `.git`、`.obsidian` 的文件，逐项检查以下四类问题。

## 检查项目

### 1. 格式一致性

- **SKILL.md 格式**：source: compound 的 skill 是否遵循 compound 格式（用途+输入+输出+质量标准+常见失败）。官方 CLI skill 不管
- **项目格式**：`projects/` 下是否全部为 `startup.md + log/`，如有残留 `project.md` 则标注
- **AGENTS.md**：是否保持精简，不应超过 20 行

### 2. 孤引用

- skill 中引用的文件路径是否存在（如 `projects/<项目>/language.md`）
- 被引用文件应在项目运行时才创建的，标注为"预留入口"而非"缺失"

### 3. 未落地

- AGENTS.md 中提到的 skill 是否已安装
- skill 引用的依赖 skill 是否存在
- 根索引 `knowledge/skills/SKILL.md` 中列出的 skill 与实际目录是否一致

### 4. 冗余

- `references/` 子目录是否残留
- `knowledge/` 中是否有内容重复的文件

## 输出格式

```markdown
# 巡检报告

## 问题 N：<类别>
| 文件 | 问题 | 建议 |
|------|------|------|

## 通过的项
```

## 分类后处理

- **立即修**：格式不统一、冗余文件
- **暂缓**：非关键、不影响当前运行
- **预留**：等项目跑起来才需要的定制文件，不算问题
