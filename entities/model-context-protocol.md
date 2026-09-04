---
type: Entity
title: Model Context Protocol (MCP)
description: Anthropic 提出的 Agent 工具通訊協定，WebMCP 的參考基礎。
sources:
  - resource: https://modelcontextprotocol.io/
    title: MCP 官方網站
  - resource: https://modelcontextprotocol.io/specification/2025-11-25
    title: MCP 規格 2025-11-25
tags: [mcp, protocol, agent, tools]
---

# Model Context Protocol (MCP)

Model Context Protocol 是 Anthropic 提出的開放協定，定義 AI Agent 如何發現和使用外部工具。

簡單想像：MCP 就像 USB，定義了一個標準接口，讓不同的 Agent 可以接上不同的工具，而不用每次都重新設計連接方式。

## 核心概念

- Tool：Agent 可以呼叫的操作，有名稱、描述和參數定義
- Resource：Agent 可以讀取的資料來源
- Prompt：預設的互動模板

## 與 WebMCP 的關係

[WebMCP](../concepts/webmcp.md) 借用 MCP 的工具描述概念，但把它帶進瀏覽器原生環境。主要差異：

- MCP 是 server-client 架構，通常透過 HTTP 或 stdio 連接
- WebMCP 直接在瀏覽器頁面中運作，工具是 JavaScript 函式
- WebMCP 可沿用瀏覽器的登入狀態，MCP 需要另外處理認證
- WebMCP 草案不要求瀏覽器實作 MCP 的完整 wire protocol

## 安全原則

MCP 規格明確反對 token passthrough：第三方認證資訊不應經過 MCP client 或模型。這個原則同樣適用於 WebMCP 工具設計。
