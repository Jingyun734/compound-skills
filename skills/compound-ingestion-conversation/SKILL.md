# 摄取：对话 → raw

## 触发
用户说"按摄取 skill 处理这次对话"，或项目结项需将对话归档。

## 原则
- 保留原文，不压缩。保留元数据。不做判断、不写观点、不抽概念。
- 概念抽取是消化的事。

## 步骤
1. 确定来源（平台、参与者、时间）
2. 提取正文：核心议题、关键决策、方向转折、纠偏时刻
3. 清理：去闲聊、去重复，保留元信息
4. 输出到 `archive/ingestion/raw/YYYY-MM-DD-<slug>.md`

## Schema
yaml frontmatter: id, title, source_type: conversation, source_url, author, published_at, captured_at, content_type, status, tags。正文在 ## Raw Content 下，捕获备注在 ## Capture Notes。

## 文件命名
`YYYY-MM-DD-<slug>.md`，放在项目 `archive/ingestion/raw/`。

## 检查
元数据完整、未添加事后观点、关键决策可追溯