---
type: Concept
title: 共享記憶
description: 讓新的 Agent session 從公開 Wiki、Git 歷史與 WikiLinks 延續工作的可追溯知識。
tags: [hatwiki, shared-memory, agents, git, wikilinks]
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
  - id: source-ingestion-contract
    resource: https://github.com/daubas/hatwiki/blob/main/docs/contracts/source-ingestion-slice.md
    title: HatWiki text source ingestion slice contract
---

# 共享記憶

一句話：HatWiki 的 shared memory 是公開 Wiki、Git 歷史與 WikiLinks 的共同狀態，不是任何單一 Agent 的對話記憶。[^hatwiki-readme]

簡單想像：把聊天裡值得留下的判斷寫進一本有版本的共同筆記；下一位 Agent 先讀筆記、沿著連結，再繼續工作。

## 三個持久層

1. **公開 Wiki**：提供頁面內容、來源引用、revision，以及由頁面連結推導出的 WikiLinks 與 backlinks。匿名網站和匿名 WebMCP 都從這個公開投影讀取。[^public-read-contract]
2. **Git 歷史**：是 Wiki 知識的 canonical 狀態；commit 保存修改內容和可稽核歸因。R2 是公開讀取用的投影，不是另一份 canonical Wiki。
3. **WikiLinks 與標準 Markdown links**：把頁面之間的關係留下來，讓新的 session 能從一頁走到相關概念，而不是只依賴搜尋結果。

## 新 session 如何接續

1. 先用公開的 `search_wiki` 找到相關頁面，再用 `read_page` 讀取頁面與 revision。
2. 沿著引用、WikiLinks 和標準 Markdown links 閱讀相鄰概念；需要核對變更時，再回看 Git revision 與歷史。
3. 不把上一個 session 的聊天內容當作 canonical context；能被下一個 session 依賴的內容，必須已經寫入公開 Wiki 或 Git。

私密來源本文不屬於公開 shared memory。登入 GitHub 並完成公開授權聲明後，使用者可以把一份 plain-text 私密來源交給既有頁面的編輯流程；來源本文仍留在 owner-scoped 私有儲存，公開頁面只保留可見的引用或 unavailable reference。[^source-ingestion-contract]

詳見 [HatWiki](/concepts/hatwiki.md) 與 [開始使用 HatWiki](/guides/getting-started.md)。

[^hatwiki-readme]: [HatWiki README](https://github.com/daubas/hatwiki/blob/main/README.md)。
[^public-read-contract]: [Public read slice contract](https://github.com/daubas/hatwiki/blob/main/docs/contracts/public-read-slice.md)。
[^source-ingestion-contract]: [Text source ingestion slice contract](https://github.com/daubas/hatwiki/blob/main/docs/contracts/source-ingestion-slice.md)。
