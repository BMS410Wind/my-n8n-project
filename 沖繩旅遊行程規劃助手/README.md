# 🏝️ 沖繩旅遊行程規劃助手
Okinawa Travel Planning Assistant

2025 NYCU AI 新秀計畫｜生成式 AI 理論與應用實務  
第三組：林汯錕、周秉毅、陳柏宏

---

## 📌 專案簡介（Overview）

沖繩旅遊行程規劃助手是一個結合 n8n（Nodemation）、RAG（Retrieval-Augmented Generation）與 AI Agent 的智慧旅遊輔助系統，可根據使用者需求，自動整合多來源旅遊資料，產生個人化的沖繩旅遊行程建議。

本專案核心目標為：
- 建立可擴充的 AI Agent 架構
- 實作 RAG 降低語言模型幻覺
- 透過 n8n 實現自動化資料處理流程
- 展示生成式 AI 在旅遊情境的實務應用

---

## 🎯 專案特色（Features）

- RAG 架構：結合向量資料庫進行知識檢索
- n8n 自動化工作流程（Nodemation）
- 多來源旅遊資料蒐集與整理
- AI Agent Supervisor 與 System Prompt 設計
- 行程、天氣、記帳整合
- 支援中英雙語輸出
- 模組化、可擴充架構

---

## 🧩 系統架構（System Architecture）

使用者 → AI Agent → RAG 檢索 → Vector Database → Embedding Tool（Ollama）→ 旅遊資料來源

資料來源包含官方旅遊網站、旅行社網站與旅遊部落格文章。

---

## 🔄 工作流程（Workflows）

### Main Flow
1. 使用者輸入旅遊需求
2. AI Agent 解析需求與上下文
3. 透過 RAG 從向量資料庫檢索相關資訊
4. 生成旅遊建議與行程規劃結果

### MCP Server Flow
- 天氣查詢
- 記帳功能
- 行程表整合
- 圖像生成工具（GenImage Tool）

### Embedding Flow
- Manual Embedding：人工整理資料後嵌入
- Automatic Embedding：n8n AI Agent 自動搜尋網站並擷取重點資訊後嵌入

---

## 📚 資料蒐集（Data Collection）

### 資料來源
- 官方旅遊網站
- 旅行社網站
- 旅遊部落格與心得文章

### 蒐集方式
- 人工整理與審核
- n8n AI Agent 自動搜尋與關鍵資訊擷取

---

## 🧠 Embedding 與向量資料庫（Vector Database）

- Embedding Tool：Ollama Embedding
- 將旅遊相關文本轉為向量後存入向量資料庫
- 提供 RAG 檢索使用

啟動 Ollama： ollama serve


---

## 🧾 AI Agent System Prompt 設計

本專案的 System Prompt 設計採用以下 10 項核心技巧：

1. Persona–Task–Context–Format 結構
2. Persona Anchoring（角色與語氣固定）
3. RAG Context Framing（限制資料來源）
4. Format Constraining（輸出格式控制）
5. Few-shot Example Learning
6. Prompt Coaching（主動詢問缺失資訊）
7. Understanding Confirmation（理解確認）
8. Instruction Guardrail（防止幻覺）
9. Semantic Anchoring（語義錨定）
10. Bilingual Framing（中英雙語穩定性）

---

## 🛠️ 使用技術（Tech Stack）

- n8n（Nodemation）
- Large Language Model（Gemini / LLM）
- Retrieval-Augmented Generation（RAG）
- Ollama Embedding
- Vector Database
- Prompt Engineering

---

## 🚀 快速開始（Quick Start）

1. Clone 專案
2. 啟動 n8n
3. 啟動 Ollama Embedding Server
4. 匯入 n8n Workflows
5. 與 AI 旅遊助理互動

---

## 📄 授權（License）

本專案僅供學術研究與課程展示使用。  
如需商業用途，請先取得作者同意。

---

## 🙌 致謝（Acknowledgements）

NYCU AI 新秀計畫  


