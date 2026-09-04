---
type: Method
title: WebMCP 權限設計模式
description: 處理 WebMCP 工具讀寫權限與授權的常見模式。
tags: [webmcp, permissions, security, patterns]
---

# WebMCP 權限設計模式

設計 [WebMCP](../concepts/webmcp.md) 工具時，需要決定哪些操作開放給匿名使用者、哪些需要登入、哪些需要額外確認。

## 三層權限模型

### 第一層：匿名唯讀

未登入使用者與其 Agent 可以使用的工具：
- 搜尋公開內容
- 閱讀公開頁面
- 瀏覽關聯圖

### 第二層：登入讀寫

已登入使用者與其 Agent 可以使用的工具：
- 編輯一般頁面
- 加入來源
- 查看自己的操作紀錄

### 第三層：管理者操作

需要特定權限的工具：
- 處理編輯衝突
- 變更受保護頁面
- 管理存取政策

## 實作重點

- 工具在註冊時可透過 annotation 標示是否需要登入
- 伺服器端必須獨立驗證每次工具呼叫的權限，不能只信任前端 annotation
- 登入狀態來自瀏覽器的 cookie / session，不來自工具參數
- 同一個工具在不同登入狀態下可以回傳不同結果（例如搜尋結果包含或排除草稿）

## 與 GitHub 的整合

詳見 [WebMCP 與 GitHub 身分整合](webmcp-github-identity.md)。
