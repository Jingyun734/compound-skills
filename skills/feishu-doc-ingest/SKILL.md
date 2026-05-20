---
name: feishu-doc-ingest
description: "飞书文档摄取：从飞书文档 URL 抓取内容，转换为标准化 Markdown 存入 knowledge/raw/。保留链接和资源文件，过滤二维码。"
source: compound
---

# 飞书文档摄取

## 触发条件

用户提供飞书文档 URL（`*.feishu.cn/docx/*` 或 `*.feishu.cn/wiki/*`），说"摄取""摄入""拉取""保存"等。

## 前置条件

- `lark-cli` 已安装并认证
- `knowledge/raw/` 目录存在

## 执行流程

### 1. 抓取文档

```bash
lark-cli docs +fetch --api-version v2 --doc "文档URL" --detail full
```

### 2. 解析 XML → Markdown

将返回的 `data.document.content` 中的 XML 转为可读 Markdown：

| XML 元素 | 转换规则 |
|----------|---------|
| `<title>` | `# 标题` |
| `<h1>` ~ `<h6>` | `#` ~ `######` |
| `<p>` | 段落，保留内联格式 |
| `<b>` / `<strong>` | `**粗体**` |
| `<em>` / `<i>` | `*斜体*` |
| `<a href="...">` | `[文本](url)` 保留链接 |
| `<img>` | 提取 href 作为图片链接 |
| `<ul>` / `<ol>` / `<li>` | Markdown 列表 |
| `<table>` / `<tr>` / `<td>` | Markdown 表格 |
| `<pre>` / `<code>` | 代码块 |
| `<callout>` | `> **emoji 标题**\n> 内容` |
| `<grid>` / `<column>` | 展开为段落/图片组合 |
| `<hr>` | `---` |
| `<cite>` | `[标题](wiki/doc URL)` 转为可点击链接 |

### 3. 元信息提取

在文件头部写入：

```markdown
# 文档标题

## 原文信息
- 飞书文档: <原始URL>
- 摄取日期: YYYY-MM-DD
```

### 4. 资源处理

- **图片**：用 `![描述](下载链接)` 直接嵌入，显示为图片
- **附件/ZIP**：单独列出在 `## 资源文件` 章节
- **二维码/公众号推广图**：删除，不保留

### 5. 链接保留

- 文档内嵌的飞书文档/知识库链接（`<cite>` 标签）转为完整飞书 URL
- 外部 HTTP 链接原样保留
- 文末附 `## 外部链接清单`，去重列出所有外链

### 6. 写入

```bash
# 文件名：{文档主题}_摄取.md
写入 knowledge/raw/{文件名}
```

## 命名规则

- 从 title 提取主题词，格式：`主题_摄取.md`
- 中文名保留，去特殊字符
- 如遇重名，加数字后缀

## 输出示例

```markdown
# Anthropic长程应用开发中的驾驭框架设计

## 原文信息
- 飞书文档: https://lcnaoyjp4e3z.feishu.cn/docx/JUT8d3Zfuoul...
- 摄取日期: 2026-05-20

## 资源文件
- 某 skill ZIP: [下载](https://internal-api-drive-stream.feishu.cn/...)

![流程图](https://internal-api-drive-stream.feishu.cn/...)
![架构图](https://internal-api-drive-stream.feishu.cn/...)

## 正文内容
...

## 外部链接清单
- https://github.com/xxx
- https://www.anthropic.com/xxx
```

## 边界处理

- 文档内容超过 50KB：截断并在末尾标注 `[内容截断，剩余部分见原文]`
- XML 解析失败：保存原始 XML 到 raw，标注 `[自动解析失败，需人工处理]`
- 链接失效：保留链接文本和 URL，标注 `[链接可能失效]`
- 图片无法访问：保留 `href` 链接，不判断可访问性
