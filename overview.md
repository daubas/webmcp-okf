---
type: Overview
title: WebMCP 知識庫
description: 整理 WebMCP 規格、瀏覽器 Agent 互動、工具設計與實踐案例的公開知識庫。
---

# WebMCP 知識庫

本知識庫持續整理 WebMCP 的規格演進、瀏覽器 Agent 互動設計、權限模型、開發實作與社群案例。

WebMCP 讓網站透過標準 API 向瀏覽器中的 AI Agent 提供工具，使人與 Agent 能在同一個網頁中協作。詳見 [WebMCP](concepts/webmcp.md)。

## 主要概念

- [WebMCP](concepts/webmcp.md)：Web 標準草案，讓網站向 Agent 註冊工具
- [Tool Registration](concepts/tool-registration.md)：網站如何宣告可供 Agent 呼叫的工具
- [Agent Session 與身分](concepts/agent-session-identity.md)：Agent 如何繼承瀏覽器登入狀態
- [人機協作模式](concepts/human-agent-collaboration.md)：人與 Agent 在同一介面中的分工

## 重要實體

- [Chrome WebMCP 實作](entities/chrome-webmcp.md)：Chrome 瀏覽器的 WebMCP API 實作
- [WebMCP Challenge](entities/webmcp-challenge.md)：Devpost 上的 WebMCP 開發競賽
- [MCP 規格](entities/model-context-protocol.md)：WebMCP 所參考的 Model Context Protocol

## 實作指引

- [註冊 WebMCP Tool](methods/registering-webmcp-tools.md)：實作 Tool Registration 的開發指引
- [WebMCP 權限設計](methods/webmcp-permission-patterns.md)：處理讀寫權限與授權的常見模式
- [WebMCP 與 GitHub 身分整合](methods/webmcp-github-identity.md)：以 GitHub OAuth 作為 WebMCP 寫入授權
