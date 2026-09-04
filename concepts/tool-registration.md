---
type: Concept
title: Tool Registration
description: 網站向瀏覽器 Agent 宣告可用工具的機制。
sources:
  - resource: https://webmachinelearning.github.io/webmcp/
    title: WebMCP Draft Community Group Report
  - resource: https://developer.chrome.com/docs/ai/webmcp/imperative-api
    title: Chrome WebMCP Imperative API
tags: [webmcp, tool, registration]
---

# Tool Registration

Tool Registration 是 [WebMCP](webmcp.md) 的核心操作：網站透過 JavaScript 告訴瀏覽器「這個頁面有哪些工具可以給 Agent 使用」。

簡單想像：就像餐廳門口的菜單，讓 AI 助手知道這裡能點什麼、每道菜需要什麼材料。

## 運作方式

網站呼叫 document.modelContext.registerTool()，傳入：

- name：工具名稱，例如 search_wiki
- description：工具用途的自然語言描述
- inputSchema：參數的 JSON Schema 定義
- execute：實際執行工具的 callback function

Agent 從 document.modelContext.tools 取得所有已註冊工具。

## 宣告式與命令式

WebMCP 同時定義兩種方式：

- 宣告式（Declarative）：透過 HTML meta 或 JSON 靜態描述工具，適合唯讀查詢。
- 命令式（Imperative）：透過 JavaScript API 動態註冊，適合需要認證、狀態或複雜互動的工具。

目前大多數實作採用命令式 API，因為多數有意義的工具都需要存取網站的執行環境。

## 設計原則

- 工具描述要讓 Agent 能判斷何時該用、需要什麼輸入。
- 把讀取與寫入分成不同工具，方便 Agent 和使用者區分風險。
- 寫入工具加上 annotation 標示影響範圍。
- 回傳的結果應有結構，而非只有純文字。
