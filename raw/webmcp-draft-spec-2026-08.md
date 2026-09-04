---
type: SourceSnapshot
title: WebMCP Draft Community Group Report 摘要
resource: https://webmachinelearning.github.io/webmcp/
captured: 2026-09-04
---

# WebMCP Draft Community Group Report

WebMCP 是 Web Machine Learning Community Group 的 Draft Community Group Report。

核心 API：
- document.modelContext：頁面的 ModelContext 介面
- registerTool(name, options)：註冊工具
- tools：已註冊工具清單

工具定義包含：
- name：字串
- description：自然語言描述
- inputSchema：JSON Schema
- execute：callback function，接收 inputObject 與 options（目前只有 AbortSignal）

安全假設：Agent 繼承瀏覽器中使用者的登入狀態。

開放議題：
- #44：動作權限
- #87：session/auth context
- #96：agent-to-tool trust
- #105：Agent 身分識別
- #257：待討論

狀態：Draft，非 W3C Recommendation。
