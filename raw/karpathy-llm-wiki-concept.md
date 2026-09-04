---
type: SourceSnapshot
title: Karpathy LLM Wiki 原始構想摘要
resource: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
captured: 2026-09-04
---

# Karpathy LLM Wiki 原始構想

Andrej Karpathy 提出的 LLM Wiki 概念：

- 原始來源保持不變
- LLM 把來源整理成持續更新的 Wiki
- 新來源不只產生摘要，而是更新既有概念頁
- 人負責挑選來源、提出問題和判斷
- LLM 負責摘要、連結、歸檔、修訂和檢查
- 有價值的查詢結果寫回 Wiki

核心洞見：知識庫不是每次從零檢索原始文件（傳統 RAG），而是讓 LLM 持續維護一套整理過的 Wiki。
