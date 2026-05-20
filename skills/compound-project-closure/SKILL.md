# 项目结项流程

## 触发
项目交付物完成，用户说"结项"。

## 前置
contract.md 已存在。archive/ 下中间产物已归位。

## 第1步：摄入
按 `compound-ingestion-conversation` 执行，产出 raw 文件。

## 第2步：消化
2.1 `compound-digestion-summary` → 摘要
2.2 `compound-digestion-extract-concepts` → 概念卡
2.3 `compound-digestion-map-concepts` → 去重映射
2.4 更新本项目 `archive/ingestion/knowledge/index.md`

## 第3步：交付
3.1 `compound-output-project` → project.md
3.2 `compound-output-review` → 复盘.md
3.3 `compound-output-knowledge` → 知识.md

## 第4步：同步
`compound-digestion-update-index` → 更新 `knowledge/index.md`

## 第5步：更新 heartbeat
在 `heartbeat/project_patterns.md` 新增一行项目记录。

## 结项检查
raw已摄入、摘要已写、概念卡已抽取映射、project/复盘/知识已写、index已同步、patterns已更新