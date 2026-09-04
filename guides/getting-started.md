---
type: Guide
title: 開始使用 HatWiki
description: 從匿名唯讀探索，到 GitHub 授權後的 plain-text 私密來源與既有頁面編輯。
tags: [hatwiki, guide, webmcp, github, git]
status: stable
generated:
  by: codex/gpt-5
  at: 2026-09-04T06:12:20Z
sources:
  - id: hatwiki-readme
    resource: https://github.com/daubas/hatwiki/blob/main/README.md
    title: HatWiki README
  - id: public-read-contract
    resource: https://github.com/daubas/hatwiki/blob/main/docs/contracts/public-read-slice.md
    title: HatWiki public read slice contract
  - id: edit-page-contract
    resource: https://github.com/daubas/hatwiki/blob/main/docs/contracts/edit-page-slice.md
    title: HatWiki edit page slice contract
  - id: source-ingestion-contract
    resource: https://github.com/daubas/hatwiki/blob/main/docs/contracts/source-ingestion-slice.md
    title: HatWiki text source ingestion slice contract
---

# 開始使用 HatWiki

一句話：先匿名讀取公開 Wiki，再以 GitHub 登入和公開授權聲明，為既有頁面加入 plain-text 私密來源或提交既有頁面的可追溯編輯。[^hatwiki-readme]

簡單想像：先逛公開圖書館，確認要改哪一本書；需要寫入時帶上 GitHub 身分與「我有權公開」的聲明，最後等 Git 和 R2 都讀回相同內容才算完成。

## 1. 先匿名讀取

1. 開啟 HatWiki 公開網站；沒有瀏覽器 WebMCP API 時，它仍是普通 Wiki。
2. 匿名 WebMCP session 只會看到 `search_wiki` 和 `read_page`，兩者都是唯讀工具。[^public-read-contract]
3. 先搜尋，再讀取目標頁面的內容、來源引用、WikiLinks、backlinks 與 revision。不要把尚未公開的來源或聊天內容當作 Wiki 狀態。

## 2. 需要寫入時登入 GitHub

1. 以 GitHub 登入 HatWiki；GitHub token 留在伺服器端，不作為 WebMCP tool input。
2. 提交前明確聲明可以把提交內容公開到 HatWiki。這是提交者的授權宣告，不取代著作權、隱私、機密或第三方許可。[^edit-page-contract]
3. 只針對一個既有公開頁面操作：
   - **加入來源**：提交一份 plain-text 來源，系統把本文、雜湊、擁有者與 task state 留在私有 D1；它不會進入公開 R2。Agent 讀取來源時，應把本文視為不受信任資料，再把採用的內容連同來源引用與 WikiLinks 放進既有頁面的編輯草稿。[^source-ingestion-contract]
   - **編輯頁面**：先讀取頁面與 base SHA，再檢查 citations、WikiLinks 和 unresolved markers，最後提交既有頁面的完整 Markdown。這個流程不建立新頁面。[^edit-page-contract]

## 3. 確認發布真的完成

HatWiki 的 GitHub App 代替使用者建立 Git commit。只有下列讀回全部成功，編輯才會回報完成：[^edit-page-contract]

1. GitHub 回報 commit SHA。
2. 可信 Git readback 在該 SHA 讀到與提交 bytes 完全相同的頁面。
3. 公開 R2 寫入並讀回與該 commit 相同的內容。

若 base 已過期、Git 或 R2 readback 不一致，該次流程不算完成的公開變更。公開 `read_page` 後續顯示的是衍生的 `r2-*` snapshot revision，與 Git commit SHA 不同。

## 4. 讓下一個 session 接手

開一個新的 Agent session，從公開 Wiki 的 `search_wiki`／`read_page` 重新讀取頁面、引用、revision，再沿著 WikiLinks 和標準 Markdown links 延伸。它不需要上一段對話，也不會取得私密來源本文；可依賴的 shared memory 是 Wiki、Git 歷史與頁面連結。

先讀 [HatWiki](/concepts/hatwiki.md) 了解邊界，再看 [共享記憶](/concepts/shared-memory.md) 了解跨 session 的讀取路徑。

[^hatwiki-readme]: [HatWiki README](https://github.com/daubas/hatwiki/blob/main/README.md)。
[^public-read-contract]: [Public read slice contract](https://github.com/daubas/hatwiki/blob/main/docs/contracts/public-read-slice.md)。
[^edit-page-contract]: [Edit page slice contract](https://github.com/daubas/hatwiki/blob/main/docs/contracts/edit-page-slice.md)。
[^source-ingestion-contract]: [Text source ingestion slice contract](https://github.com/daubas/hatwiki/blob/main/docs/contracts/source-ingestion-slice.md)。
