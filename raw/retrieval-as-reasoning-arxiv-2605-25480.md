---
type: SourceSnapshot
title: "Retrieval as Reasoning: Self-Evolving Agent-Native Retrieval via LLM-Wiki 摘要"
resource: https://arxiv.org/abs/2605.25480
captured: 2026-09-04
---

# Retrieval as Reasoning

論文提出 Agent 透過 LLM Wiki 進行檢索即推理：

- Agent 不只做向量搜尋，而是透過搜尋、閱讀、沿連結前進和判斷證據是否足夠來組合檢索步驟
- Wiki 對需要跨文件、關係追蹤及多步推理的問題特別有價值
- 單一文件內的簡單問題，直接檢索原始文章可能更有效
- 知識庫不必以向量 RAG 為核心，但仍需要檢索能力

啟示：WebMCP 工具可以實作這種「搜尋、閱讀、導覽」的漸進式檢索模式。
