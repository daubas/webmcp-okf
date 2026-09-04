---
type: Method
title: 註冊 WebMCP Tool
description: 在網站中實作 WebMCP Tool Registration 的開發指引。
sources:
  - resource: https://developer.chrome.com/docs/ai/webmcp/imperative-api
    title: Chrome WebMCP Imperative API
tags: [webmcp, tool-registration, development]
---

# 註冊 WebMCP Tool

本頁整理在網站中實作 [Tool Registration](../concepts/tool-registration.md) 的實務指引。

## 基本流程

1. 確認頁面環境支援 WebMCP（檢查 document.modelContext 是否存在）
2. 定義工具的名稱、描述、參數 Schema 與執行函式
3. 呼叫 document.modelContext.registerTool() 註冊
4. 工具即可被瀏覽器 Agent 發現與呼叫

## 設計建議

### 工具粒度

- 每個工具做一件明確的事，避免萬用工具
- 讀取與寫入分開，方便權限控制
- 名稱用動詞開頭：search_wiki、read_page、edit_page

### 描述品質

- description 是 Agent 決定是否使用這個工具的主要依據
- 寫清楚：什麼時候該用、輸入什麼、回傳什麼
- 避免技術術語堆疊，用 Agent 能理解的自然語言

### 參數定義

- 使用 JSON Schema 定義 inputSchema
- 必要參數標示 required
- 提供合理的預設值減少 Agent 猜測

### 回傳格式

- 回傳結構化物件，而非純文字
- 包含足夠的 context 讓 Agent 理解結果
- 回傳有限的內容量，避免塞滿 Agent 的 context window

## 安全注意事項

- 寫入工具必須在伺服器端驗證使用者權限
- 不要把 token 或敏感資料放進工具參數或回傳值
- 加上 untrustedContentHint 標示外部來源內容
- 參見 [Agent Session 與身分](../concepts/agent-session-identity.md)
