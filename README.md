---
type: Reference
title: webmcp-okf
description: WebMCP 主題的公開 OKF 知識庫與 HatWiki Demo 內容來源。
tags: [webmcp, okf, hatwiki]
status: stable
generated:
  by: codex/gpt-5
  at: 2026-09-04T06:12:20Z
---

# webmcp-okf

WebMCP 主題的公開 OKF 知識庫。

整理 WebMCP 規格、瀏覽器 Agent 互動、工具設計、權限模型與實踐案例。

## 結構

- concepts/ — 核心概念與設計原則
- entities/ — 具體專案、規格與產品
- methods/ — 實作模式與開發指引
- guides/ — HatWiki 使用指引
- raw/ — 原始來源快照（不進入公開 Wiki 投影）

## 格式

使用 [OKF v0.2](https://github.com/GoogleCloudPlatform/open-knowledge-format/blob/main/SPEC.md) 的 Markdown + YAML frontmatter 格式。

每頁包含 type、title、description，引用來源列在 sources 欄位。

## 使用方式

本知識庫可以被 [HatWiki](https://github.com/daubas/hatwiki) 等 OKF Wiki 工具讀取並呈現為可搜尋、可瀏覽的知識圖譜。

也可以直接在 GitHub 上閱讀，或被任何支援 Markdown 的工具使用。

## 貢獻

歡迎透過 Pull Request 或 Issue 貢獻內容。新來源請先放 raw/，整理後合併到對應目錄。
