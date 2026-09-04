---
type: Concept
title: WebMCP
description: 讓網站向瀏覽器 Agent 提供結構化工具的 Web 標準草案。
sources:
  - resource: https://webmachinelearning.github.io/webmcp/
    title: WebMCP Draft Community Group Report
  - resource: https://developer.chrome.com/docs/ai/webmcp
    title: Chrome WebMCP 文件
tags: [webmcp, browser-agent, web-standard]
---

# WebMCP

WebMCP 是 Web Machine Learning Community Group 提出的草案標準，讓網站能透過 JavaScript API 向瀏覽器中的 AI Agent 宣告和提供工具。

簡單想像：一個網站可以告訴瀏覽器裡的 AI 助手「我這邊有搜尋、編輯、查詢三種工具可以用」，AI 助手就能根據使用者的指令呼叫這些工具。

## 核心機制

1. 網站透過 document.modelContext.registerTool() 註冊工具，包含名稱、描述、參數定義與執行函式。
2. 瀏覽器 Agent 發現頁面上可用的工具清單。
3. Agent 根據使用者指令選擇並呼叫合適的工具。
4. 工具在網站的安全環境中執行，結果回傳給 Agent。

詳見 [Tool Registration](tool-registration.md)。

## 與 MCP 的關係

WebMCP 參考 [Model Context Protocol](../entities/model-context-protocol.md) 的工具定義格式，但並非要求瀏覽器實作完整的 MCP wire protocol。它將 MCP 的工具描述與呼叫概念帶進瀏覽器原生 API。

## 安全模型

Agent 沿用使用者在瀏覽器中既有的登入狀態（cookie、session）。網站能驗證目前登入的使用者身分，但目前草案無法讓網站驗證是哪一個 Agent 在呼叫工具。詳見 [Agent Session 與身分](agent-session-identity.md)。

## 現況

WebMCP 是 Draft Community Group Report，不是 W3C Recommendation。Chrome 已有實作，其他瀏覽器尚在觀望。API 仍在快速演進。
