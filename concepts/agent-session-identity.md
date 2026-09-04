---
type: Concept
title: Agent Session 與身分
description: 瀏覽器 Agent 如何繼承網站登入狀態，以及目前身分驗證的限制。
sources:
  - resource: https://webmachinelearning.github.io/webmcp/
    title: WebMCP Draft Community Group Report
  - resource: https://github.com/webmachinelearning/webmcp/issues/96
    title: "WebMCP issue #96: agent-to-tool trust"
tags: [webmcp, identity, session, security]
---

# Agent Session 與身分

在 [WebMCP](webmcp.md) 架構下，瀏覽器 Agent 呼叫網站工具時，會沿用使用者在該網站的登入狀態。

簡單想像：Agent 就像一個替你操作網頁的助手，它用的是你已經登入的帳號，不是它自己的帳號。

## 目前能驗證什麼

- 網站可以驗證目前的登入使用者（透過 cookie / session）。
- 伺服器可以確認使用者對特定資源的權限（例如 GitHub repo 權限）。

## 目前無法驗證什麼

- 無法確認呼叫工具的是哪一個 Agent（ChatGPT、Gemini、Codex 等）。
- 無法驗證 Agent 的模型版本。
- 無法確認人類是否真的授權了這次操作。
- 無法跨工具呼叫建立可信的 session ID。

這些缺口正在 WebMCP 社群討論中（issue #44、#87、#96、#105），但尚未成為正式 API。

## 實務影響

設計 WebMCP 工具時，應假設：

- 信任的單位是「已登入的網站使用者」，不是「Agent」。
- Agent 自我聲明的名稱只作參考，不可用於授權判斷。
- 寫入操作仍需在伺服器端驗證使用者權限。
- Token 不應傳進工具參數或 Agent context。
