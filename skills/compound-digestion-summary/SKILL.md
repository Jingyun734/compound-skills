# 消化：写摘要

## 触发
raw/ 有新增文件。

## 原则
摘要不是再写一遍原文，是编译成可检索的结构。保留来源引用，按主题组织不按时序。

## 步骤
1. 读 raw，理解完整内容
2. 提取 3-5 个核心观点
3. 每个观点附原文证据
4. 提开放问题：材料未回答但值得追问的
5. 输出到 `archive/ingestion/knowledge/summary-YYYY-MM-DD-<slug>.md`

## Schema
yaml: id, title, type: summary, project, created_at, source_id。正文含 ## Core Idea、## Key Points、## Open Questions、## Source。

## 检查
引用了 raw 来源、不重复原文、开放问题已列出