# 消化：抽取概念

## 触发
摘要完成，raw 已理解。

## 原则
从 raw 中识别可独立存在的知识单元。每卡一概念（Atomic Notes）。先查已有概念再决定新建还是映射。

## 步骤
1. 读 raw 和摘要
2. 识别候选概念：能脱离原文独立理解的判断/定义/规律
3. 搜索 `knowledge/concepts/` 和项目已有概念卡
4. 已有→映射；新概念→在 `archive/ingestion/knowledge/` 建卡
5. 冲突→标记，不覆盖

## 概念卡 schema
yaml: id, title, type: concept, project, created_at, status: candidate, sources。正文含 ## Definition、## Why It Matters、## 验证状态。

## 检查
每卡一主题、已查重、冲突已标记、来源可追溯