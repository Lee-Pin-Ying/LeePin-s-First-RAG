# LeePin’s First RAG｜機器學習筆記問答助教

以《機器學習第五週筆記》建立知識庫，先搜尋相關內容，再由 LLM 根據筆記回答，並顯示引用與來源頁碼。

## 資料整理

透過 ChatGPT 輔助，依主題整理成 **31 個文字區塊**，移除目錄、重複頁尾，整理表格並核對公式。每個區塊以 JSON 保存正文、來源文件、頁碼與章節，未使用固定字數切分或固定重疊。

## 檔案用途

| 檔案 | 用途 |
|---|---|
| RAG01 Notebook | 建立文件向量、測試檢索並匯出知識庫 |
| RAG02 Notebook | 自動下載知識庫、呼叫 LLM，並提供 Gradio 介面 |
| `documents.json` | 31 個區塊的正文與來源資訊 |
| `ml_week5_vectorDB.zip` | FAISS 索引、正文、編號對照與模型設定 |
| 機器學習第五週筆記 PDF | 原始資料 |

## 執行方式

1. 使用 Google Colab 開啟 **RAG02 Notebook**，依序執行程式格。
2. 程式會從 Google Drive 公開連結自動下載知識庫，不需先執行 RAG01。
3. 在隱藏輸入欄填入自己的 **Groq API key**，再啟動 Gradio 問答介面。

本次使用本機 **NVIDIA GeForce RTX 5060 Laptop GPU** 執行 embedding。Gradio 服務需保持執行階段開啟，並非永久網站。

## 使用技術

- Embedding：`google/embeddinggemma-2`，每個區塊產生 768 維向量。
- 檢索：FAISS `IndexFlatIP`，比較正規化向量的相似度。
- 回答：AIsuite 呼叫 Groq `openai/gpt-oss-120b`。
- 介面：Gradio。

## 測試問題

- Bootstrap 為什麼平均約有 63.2% 的不同原始資料被抽到？
- Bagging 和 AdaBoost 在訓練方式及整合預測上有什麼差別？
- 老師下次期中考會考哪些題目？（筆記未提供，應說明資訊不足。）

本專案為課程練習。相似度不是答案正確率，回答仍需對照來源內容核實。
