# twstock-ai-data

「台股 AI 智慧選股工作台」（https://linhinet7451.github.io/twstock-ai/ ）的**資料專用 repo**。

網站程式在 linhinet7451/twstock-ai；本 repo 只放後端產出的靜態資料，由 GitHub Actions 自動維護，不需手動編輯：

- `data/manifest.json`：資料版本、最新行情日期、檔數
- `data/scan.json.gz`：全市場最近 370 日掃描包
- `data/history/<代號>.json.gz`：每檔完整 10 年歷史（懶載入）
- `data/state.json`：後端執行狀態

自動化：
- 每日更新（data-daily）：週一至五 18:30（台灣時間）抓 TWSE/TPEx 官方全市場行情，增量併入歷史並重建掃描包
- 歷史回補（data-backfill）：手動觸發，補新上市或缺漏的歷史
- 每月瘦身（data-squash）：每月 1 號把本 repo 的 git 歷史重置為單一 commit（資料檔案與網址不變），避免每日 commit 累積膨脹
- 一次性搬移（bootstrap）：自舊站複製既有資料（已完成，可刪除）
