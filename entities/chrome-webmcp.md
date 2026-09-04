---
type: Entity
title: Chrome WebMCP 實作
description: Google Chrome 瀏覽器中的 WebMCP API 實作現況。
sources:
  - resource: https://developer.chrome.com/docs/ai/webmcp
    title: Chrome WebMCP 文件
  - resource: https://developer.chrome.com/docs/ai/webmcp/imperative-api
    title: Chrome WebMCP Imperative API
  - resource: https://developer.chrome.com/docs/ai/agents
    title: Chrome AI agents 文件
tags: [chrome, webmcp, browser, implementation]
---

# Chrome WebMCP 實作

Chrome 是目前唯一公開實作 [WebMCP](../concepts/webmcp.md) API 的主流瀏覽器。

## 可用 API

- document.modelContext.registerTool()：註冊工具
- document.modelContext.tools：列出已註冊工具
- 支援命令式（Imperative）與宣告式（Declarative）兩種 [Tool Registration](../concepts/tool-registration.md)

## 目前狀態

Chrome 的實作追蹤 WebMCP Community Group Draft，API 可能隨草案修改而變動。開發者需注意瀏覽器版本差異與 feature flag 設定。

## Agent 支援

Chrome 內建的 AI 功能（如 Gemini）可以發現並呼叫頁面上的 WebMCP 工具。第三方 Agent（如 ChatGPT 瀏覽器模式）的支援程度取決於各 Agent 實作。
