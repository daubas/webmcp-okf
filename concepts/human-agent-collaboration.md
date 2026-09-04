---
type: Concept
title: 人機協作模式
description: 人與 Agent 在同一個 WebMCP 網站中的分工與互動模式。
tags: [webmcp, collaboration, human-agent]
---

# 人機協作模式

[WebMCP](webmcp.md) 的產品價值不只是讓 Agent 能讀取網站資料，而是讓人與 Agent 在同一個介面中各司其職。

簡單想像：人和 AI 助手坐在同一張桌子前，桌上有相同的工具和資料。人負責決定方向和判斷品質；AI 負責搜尋、整理和執行重複性工作。

## 三種常見分工

### 1. Agent 讀取，人決策

Agent 透過 WebMCP 搜尋和閱讀資料，整理後呈現給人做最終判斷。網站只提供讀取工具。

### 2. Agent 提案，人核准

Agent 透過 WebMCP 提出修改建議（例如編輯 Wiki 頁面），網站在人核准前暫存候選版本。人在 UI 上看 diff 後決定是否採用。

### 3. Agent 直接操作，人事後稽核

Agent 直接透過 WebMCP 執行寫入操作，但所有變更都留下 Git commit 等可追查紀錄。人事後透過版本歷史檢查和還原。

## 設計原則

- 人與 Agent 看到同一份資料狀態。
- 高風險操作（刪除、發布、變更權限）保留給人類確認。
- Agent 的操作紀錄可追查、可還原。
- 未登入使用者（含匿名 Agent）只能使用唯讀工具。
