## 2026/03/13

# n8n AI 自動化整合專案 (RAG & MCP Ecosystem)

本專案是一個基於 **n8n** 的自動化工作流集合，深度整合了 **Ollama (本地 LLM)**、**Supabase (向量資料庫)** 以及 **MCP (Model Context Protocol)**。專案目標在於建構一個具備知識庫檢索 (RAG)、工具調用 (Function Calling) 與生活助理功能的 AI 自動化環境。

## 📂 專案結構

```
.
├── docker-compose.yml     # 容器定義檔
└── workflows/             # 工作流定義檔存放區
    ├── MCP server.json
    ├── RAG CHAT BOT.json
    ├── genimage_tool.json
    ├── rag embeddings ollama.json
    ├── 天氣_記帳_行程表.json
    └── 定時抓沖繩旅遊資訊.json
```

* * *

## 🚀 快速部署步驟

### 1\. 修改環境配置

在啟動前，請編輯 `docker-compose.yml`，將其中的 `NGROK_AUTHTOKEN` 更換為你個人的 Token，以確保 Webhook 能順利穿透內網連至外部服務（如 LINE）。

### 2\. 啟動服務

於終端機執行以下指令開啟所有核心服務：

```
docker compose up -d
```

### 3\. 驗證容器狀態

請執行 `docker ps` 確認以下三個關鍵服務皆已成功運行：

- **n8n**: 流程自動化引擎 (Port: 5678)
- **ollama**: 本地大型語言模型推論引擎 (Port: 11434)
- **ngrok**: LINE 等外部服務所需的 Webhook 隧道 (Port: 4040)

* * *

## ⚙️ 工作流 (Workflow) 詳細配置指南

進入 n8n 後 (http://localhost:5678/) ，請針對各工作流手動調整相關憑證 (Credentials) 與參數：

### 1\. RAG CHAT BOT (核心對話系統)

- **AI 模型**: 重新綁定 Google Chat Model 憑證。
- **資料存儲**: 修改 Supabase (Postgres) 連線資訊與 Ollama Embeddings 憑證。
- **外部整合**:
    - 設定 LINE Webhook 連接。
    - (optional) 修改 Send Mail Node 的收件人地址。
    - 指定 Google Drive 節點的目標目錄路徑。

- **MCP**: 設定 MCP Client 的 Endpoint。

### 2\. 天氣、記帳與行程自動化

- **天氣資訊**: 修改 OpenWeatherMap API Key。
- **行程與數據**: 設定 Google Sheet (記帳) 與 Google Calendar (行程) 憑證。

### 3\. RAG 知識庫建立 (Embeddings)

- **文件檢索**: 修改 Read/Write File from Disk 節點，指定本地磁碟中欲讓模型讀取的資料路徑。
- **向量存儲**: 設定 Supabase VectorStore 憑證。

### 4\. 影像生成工具 (GenImaging\_Tool)

- **API 介接**: 修改 HTTP Request1 節點中的 HuggingFace API Token。
- **存儲**: 設定 Google Drive 憑證。

### 5\. 其他應用

- **定時沖繩旅遊資訊**: 配置 Supabase 與對應的 Google Chat Model 憑證。

* * *

## 🔧 疑難排解 (Troubleshooting)

- **Port 佔用**：請先用`sudo lsof -i -P -n | grep LISTEN`確認11434、5678、4040 端口沒有被其他程式佔用。
- **GPU 資源佔用**：若 Ollama 啟動失敗，請先執行 `nvidia-smi` 檢查顯存是否被其他進程佔用，必要時請先終止相關殘留程序。
- **Webhook 失敗**：請檢查 ngrok 狀態頁面確認網址是否已更新，並將新的網址同步至 LINE Developer Console。

<br>
