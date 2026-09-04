---
type: Method
title: WebMCP 與 GitHub 身分整合
description: 以 GitHub OAuth 作為 WebMCP 寫入授權的實作模式。
sources:
  - resource: https://docs.github.com/en/apps/creating-github-apps/authenticating-with-a-github-app/generating-a-user-access-token-for-a-github-app
    title: GitHub App User Access Token
tags: [webmcp, github, identity, oauth]
---

# WebMCP 與 GitHub 身分整合

當 WebMCP 網站以 Git Repository 作為知識庫的正式狀態時，GitHub OAuth 是目前最直接的寫入授權機制。

## 整體架構

1. 使用者透過 GitHub OAuth 登入網站
2. 網站以 GitHub App 取得 user access token
3. Token 只存在伺服器端，前端使用 HttpOnly cookie
4. WebMCP 寫入工具在伺服器端使用 token 操作 GitHub API
5. 每次寫入產生 Git commit，保留歸因與可追查性

## 身分信任邊界

能驗證的：
- GitHub 使用者身分
- 使用者對特定 Repository 的權限
- 每次操作的時間、目標與結果

不能驗證的：
- 是哪個 Agent 代使用者操作
- Agent 的模型版本
- 人類是否真的在場

因此稽核紀錄應區分：
- github_principal（已驗證）
- agent_label（自我聲明，不可用於授權）

## 安全原則

- GitHub token 絕不進入 WebMCP tool 參數或模型 context
- 伺服器端每次操作都重新驗證 session 與 Repository 權限
- Installation token（App 自己行動）與 User token（代表使用者）使用不同 auth_kind

## 參見

- [Agent Session 與身分](../concepts/agent-session-identity.md)
- [WebMCP 權限設計模式](webmcp-permission-patterns.md)
