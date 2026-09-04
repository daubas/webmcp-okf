---
type: Schema
title: WebMCP OKF Knowledge Base Schema
description: 本知識庫的結構、分類與命名規則。
---

# WebMCP OKF Knowledge Base Schema

本知識庫以 OKF v0.2 格式整理 WebMCP 相關的規格、實作、工具設計、瀏覽器 Agent 互動與案例。

## 分類

| 目錄 | 用途 | 範例 |
|---|---|---|
| concepts/ | 核心概念與設計原則 | WebMCP 是什麼、Tool Registration、Agent Session |
| entities/ | 具體的專案、組織、規格或產品 | Chrome WebMCP API、WebMCP Challenge、MCP 規格 |
| methods/ | 觀察方法、實作模式與開發指引 | 如何註冊 WebMCP Tool、權限設計模式 |
| raw/ | 原始來源快照，不進入公開 Wiki | 論文摘要、官方文件節錄 |

## 命名規則

- 檔名使用小寫英文、連字號分隔：webmcp-imperative-api.md
- 每頁必須包含 YAML frontmatter：type、title、description
- sources 欄位列出引用來源
- WikiLink 使用標準 Markdown link 格式

## 維護

- 新來源先放 raw/，整理後再合併到 concepts、entities 或 methods。
- 每次更新以 Git commit 留下可追查紀錄。
- 公開投影不包含 raw/ 目錄。
