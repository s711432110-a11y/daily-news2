# DailyPulse 每日脈動 · 全方位新聞儀表板

> **作業主題**：建立一個自己的 `AGENTS.md` 或 `CLAUDE.md`，並完成一個可實際瀏覽的新聞儀表板成果。

---

## 🌟 專案亮點與核心特色

與一次性的「Vibe Coding」不同，本專案的核心目標在於**「建立一套讓 AI 能徹底理解並依循的開發規範與資料合約」**，讓未來任何 AI 代理人（Antigravity、Claude Code、Cursor、Copilot）都能依照同一套標準，光速新增新聞分類、拓展功能或改版介面。

- **現代典雅淺色雜誌風格 (Light Editorial Aesthetic)**：
  - 專為高質感閱讀設計，以冷壓石板白（Off-White）與純白卡片為基底，告別沉重黑底，具備類似 Financial Times 與 Apple News 的細膩雜誌質感。
  - 微立體投影、精緻分類彩色邊條與平滑懸浮回饋。
  - 深淺色模式一鍵自由切換（預設為典雅淺色）。
- **七大精緻新聞板塊（每個板塊皆收錄至少 5 則以上高質量新聞，全站共 35 則）**：
  1. 🚨 **重大事件 (Major Events)**：跨領域重大焦點（聯合國AI安全公約、跨國海底電纜協議、諾貝爾醫學獎突破、COP氣候峰會、超音速客機法規）
  2. 📊 **財金焦點 (Finance)**：央行利率決策、通膨走勢、外匯存底新高、出口連紅數據、IMF全球總經預測
  3. 📰 **時事要聞 (Current Events)**：基礎設施防護法三讀、亞太經貿高峰會、智慧區域電網、都會通勤月票常態化、偏鄉遠距醫療健保給付
  4. 📈 **股市觀測 (Stock Market)**：台股先進封裝概念股、美股科技巨頭資本支出、台積電法說展望、水冷散熱模組訂單、創新板法規鬆綁
  5. 🎭 **娛樂生活 (Entertainment)**：金馬影展入圍名單揭曉、台北大巨蛋演唱會經濟實名制、台灣原創影集海外奪冠、高流沉浸式聲光展、文化禮金效益
  6. 📑 **會計與審計 (Accounting)**：新版審計準則公報強化舞弊查核、四大會計師事務所 IFRS S1/S2 永續確信、CFC 反避稅查核、審計委員會獨立性新規、生成式AI審計指引
  7. ⚠️ **ESG 負面新聞 (ESG Risk)**：獨家配備**「ESG 風險雷達監控面板」**，即時追蹤企業環境排污勒令停工、重大工安吊掛事故勞檢、上櫃生技內線交易搜索、餐飲勞基法未付加班費開罰、跨國快時尚漂綠調查
- **互動與實用功能**：
  - **即時全文搜尋檢索**：支援標題、來源、摘要與標籤即時比對。
  - **AI 核心要點精粹彈窗 (Modal)**：點擊任一卡片立即展開重點摘要條列。
  - **一鍵複製 Markdown 簡報**：直接複製今日完整 7 大板塊報告至剪貼簿。
  - **純前端零依賴（Zero-Build / Zero-Backend）**：不需安裝 Python、Node.js，直接雙擊 `index.html` 即可瀏覽，100% 相容 GitHub Pages！

---

## 📂 專案檔案結構

```
daily_news/
├── AGENTS.md                  # 專案最高規範（AI 開發指引、設計系統、資料合約、擴充 SOP）
├── CLAUDE.md                  # Claude Code 快速參考手冊
├── README.md                  # 專案說明與 GitHub 部署教學
├── index.html                 # 儀表板前端核心結構 (純 HTML5)
├── css/
│   └── style.css              # 現代典雅淺色設計系統樣式檔（變數、立體卡片、動態）
├── js/
│   └── app.js                 # 核心控制邏輯（七大板塊資料集、搜尋、分類篩選、彈窗、匯出）
├── data/                      # 結構化資料備份
│   └── latest.json
└── scripts/                   # 爬蟲腳本備援
    └── fetch_news.py
```

---

## 🚀 如何在本地直接開啟預覽

本專案採純靜態設計，無需執行任何安裝指令：
1. 直接在電腦資料夾中找到 `index.html`。
2. **連按滑鼠左鍵兩下（雙擊）`index.html`**，即可直接用 Chrome / Edge 瀏覽器開啟完整的精緻網頁！

---

## 🌐 如何上傳至 GitHub 並啟用 GitHub Pages（線上瀏覽）

作業要求最後需**上傳至 GitHub，並提供一個可實際瀏覽的網頁成果**。請依循以下兩種方法之一：

### 推薦方法 A：直接使用 GitHub 網頁上傳（免裝 Git，最快最穩）
1. 前往 [GitHub 官網](https://github.com/) 登入您的帳號。
2. 點擊右上角的 **+** 號，選擇 **New repository**。
3. 填寫儲存庫名稱（例如 `daily-news-dashboard`），設為 **Public**，點擊 **Create repository**。
4. 在新建立的頁面中，點擊 **"uploading an existing file"**（上傳現有檔案）。
5. 將本專案資料夾內的所有檔案與資料夾（包含 `index.html`, `css/`, `js/`, `AGENTS.md`, `CLAUDE.md`, `README.md` 等）拖曳上傳至 GitHub。
6. 點擊下方的 **Commit changes** 綠色按鈕完成上傳。
7. **啟用免費網頁託管 (GitHub Pages)**：
   - 點擊儲存庫上方的 **Settings**（設定）分頁。
   - 在左側選單點擊 **Pages**。
   - 在 **Build and deployment** 下方的 **Source** 選擇 `Deploy from a branch`。
   - 在 **Branch** 下拉選單選擇 `main`，資料夾維持 `/(root)`，點擊 **Save**。
   - 等待約 1 到 2 分鐘，重新整理頁面，頂部就會出現您的專屬網址：
     👉 `https://<您的GitHub帳號>.github.io/daily-news-dashboard/`
   - 將該網址提交即可作為作業的「可以實際瀏覽的網頁成果」！

---

### 方法 B：使用 Git 命令列上傳
若電腦已安裝 Git：
```bash
# 1. 進入專案目錄
cd c:\Users\User\Desktop\daily_news

# 2. 初始化並提交
git init
git add .
git commit -m "feat: upgrade to 7 sections with light editorial theme and 35+ news items"

# 3. 推送至 GitHub（請換成您的 GitHub 儲存庫網址）
git branch -M main
git remote add origin https://github.com/<您的GitHub帳號>/daily-news-dashboard.git
git push -u origin main
```
推送完成後，依上述步驟至 **Settings -> Pages** 開啟 GitHub Pages 即可。
