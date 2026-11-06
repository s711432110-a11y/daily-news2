# AGENTS.md - DailyPulse 全方位每日新聞儀表板開發規範

> 本文件是本專案的最高指引規範（Constitution & Development Guide）。任何 AI 代理人（包含 Antigravity、Claude Code、Cursor、GitHub Copilot 等）在讀取、新增、重構或維護本專案程式碼與新聞內容時，**必須嚴格遵守本文件所定義的架構、設計風格與資料標準**。

---

## 1. 專案目的與核心願景 (Mission & Vision)

- **專案名稱**：`DailyPulse 每日脈動 · 全方位新聞儀表板`
- **核心定位**：一個無需安裝任何 Python 或後端伺服器、開箱即用、自動化分類整理並以**現代典雅淺色雜誌風格（Light Editorial Aesthetic）**精緻呈現每日重要新聞的純前端現代化新聞中心。
- **目標受眾**：需要快速掌握跨領域重要資訊的專業工作者、投資人、會計審計人員、企業決策者與研究人員。
- **七大核心分類**：
  1. **財金焦點 (Finance)**：總體經濟、各國央行利率政策、匯率變動、通膨走勢、外匯存底與國際經貿指標。
  2. **時事要聞 (Current Events)**：國內外重大公共政策、重大民生法規新制、國會法案審查與外交要聞。
  3. **股市觀測 (Stock Market)**：台股加權指數、美股四大指數、半導體供應鏈、CoWoS先進封裝、AI晶片巨頭法說會動態。
  4. **娛樂生活 (Entertainment)**：金馬金曲影展大獎評析、台北大巨蛋演唱會經濟、文化創意影劇與串流產業趨勢。
  5. **會計與審計 (Accounting)**：審計準則公報修訂、IFRS S1/S2 永續確信接軌、受控外國企業（CFC）反避稅查核、四大會計師事務所觀點。
  6. **ESG 負面新聞 (ESG Risks & Controversies)**：企業環境污染排放開罰、重大工安職災與勞動檢查勒令停工、公司治理內線交易弊端、漂綠爭議監警。
  7. **重大事件焦點 (Major Events & Cross-Domain)**：**新增跨領域重大事件板塊**，收錄不受單一分類限制的國內外重大突發要聞（如全球地緣政治震盪、國際重大天災警報、諾貝爾獎項公布、前瞻科技重大突破、跨國大型合作協議）。
- **非一次性 Vibe Coding 聲明**：
  本專案並非拋棄式的單頁網頁，而是一套**具備資料合約（Data Contract）、模組化前端結構與持續擴展規則**的系統架構。未來任何 AI 只要依循此規範，即可持續擴充新區塊、加入新新聞來源、改版介面或新增分析功能。

---

## 2. 目錄結構與檔案命名規範 (Project Structure & Naming)

本專案採**純靜態免編譯（Zero-Build / Zero-Backend）**架構，任何瀏覽器直接點開 `index.html` 即可完整運作，亦 100% 完美相容 GitHub Pages 免費託管：

```
daily_news/
├── AGENTS.md                  # 本規範文件（AI 開發指南與核心規則）
├── CLAUDE.md                  # Claude 專用對應指引（維持同步相容）
├── README.md                  # 專案介紹、GitHub 上傳步驟與 GitHub Pages 發布教學
├── index.html                 # 主儀表板網頁（包含結構、模組與內嵌/外部支援）
├── css/
│   └── style.css              # 現代典雅淺色設計系統樣式檔（CSS 變數、Glassmorphism、精緻卡片）
└── js/
    └── app.js                 # 前端互動邏輯（新聞資料集、搜尋、七大分類切換、彈窗、匯出）
```

### 檔案與命名規範：
1. **零安裝、開箱即用**：全站依賴標準 HTML5 / CSS3 / ES6+ JavaScript，不使用需 Node.js 或 Python 才能編譯的沉重工具鏈。
2. **樣式與腳本分離**：
   - 視覺外觀樣式統一收納在 `css/style.css`。
   - 資料結構與前端邏輯統一收納在 `js/app.js`（並於 `index.html` 正確引入）。
3. **命名原則**：
   - 檔案名稱一律使用小寫 kebab-case（例如 `style.css`, `app.js`）。
   - CSS 類別採用語意化命名（如 `.news-card`, `.badge--esg-high`）。
   - JavaScript 變數與函式使用 camelCase，常數使用 UPPER_SNAKE_CASE。

---

## 3. 資料合約與格式規範 (Data Schema Contract)

新聞資料集中管理於 `js/app.js` 的 `DAILY_NEWS_DATA` 物件中，任何 AI 進行內容新增時，**每個板塊必須維持至少 5 則高質量新聞，並嚴格遵守以下格式**：

```javascript
const DAILY_NEWS_DATA = {
  lastUpdated: "2026-11-06 11:30",
  dateText: "2026 年 11 月 06 日 星期五",
  heroBreakingId: "major-001", // 今日焦點頭條新聞 ID
  categories: [
    {
      id: "major_events",
      name: "重大事件",
      icon: "fa-bullhorn",
      color: "#e11d48",
      badgeClass: "badge-major",
      description: "跨領域重大焦點、突發全球政經大事件與國際焦點"
    },
    // ... finance, current_events, stock_market, entertainment, accounting, esg_risk
  ],
  news: [
    {
      id: "major-001",
      categoryId: "major_events",
      title: "聯合國通過全球前瞻人工智慧治理安全條約 70 國代表共同簽署歷史性框架",
      summary: "為防止前瞻AI科技脫序並保護全球人權與關鍵系統，各國代表歷經馬拉松談判達成共識...",
      source: "路透社 / 中央社",
      sourceUrl: "https://www.cna.com.tw/",
      publishedAt: "30 分鐘前",
      readTime: "4 分鐘",
      tags: ["全球重大焦點", "AI安全公約", "聯合國", "國際監理"],
      isBreaking: true,
      takeaways: [
        "明定前瞻模型算力通報標準與軍事致命自主武器禁用原則",
        "建立跨國演算法稽核專家小組與緊急熔斷機制",
        "國際經貿組織將把AI合規指標納入全球貿易協定審查"
      ]
    },
    {
      id: "esg-001",
      categoryId: "esg_risk",
      title: "某上市化學大廠未依許可貯存有害廢棄物 地方環保局祭出重罰勒令停工",
      summary: "環保稽查人員突擊檢驗發現未申報廢棄物直排疑慮，依水污染防治法與廢棄物清理法裁罰法定最高上限並強制停工...",
      source: "環境資訊中心",
      sourceUrl: "https://e-info.org.tw/",
      publishedAt: "2 小時前",
      readTime: "4 分鐘",
      tags: ["環保違規", "勒令停工", "水污法裁罰"],
      riskLevel: "high", // 僅限 esg_risk: "high" | "medium" | "low"
      riskDimension: "Environmental", // "Environmental" | "Social" | "Governance"
      isBreaking: false,
      takeaways: [
        "主管機關依水污法處以重罰並移送司法機關偵辦",
        "該公司預計停工產線佔營收比重約 12%，衝擊短期出貨",
        "企業內部啟動內控專案審查以補強環境合規管理"
      ]
    }
  ]
};
```

---

## 4. 網頁視覺與設計系統 (Design System & Aesthetic Guidelines)

為達成使用者要求的**「典雅精緻、背景不要深色」**之視覺要求，介面全面採用現代精品金融雜誌排版風格（參考 Financial Times 典雅白、Apple News 精緻排版與 Bloomberg 專業情報風格）：

### 4.1 色彩計畫 (Color Palette)
- **預設淺色底色 (Light Mode Default)**：
  - 全域背景：`#f8fafc`（冷壓石板白）搭配柔和漫射漸層
  - 卡片本體：`#ffffff`（純粹亮白）
  - 卡片邊框：`rgba(226, 232, 240, 0.85)` 細緻淡灰線條
  - 懸浮回饋：柔和立體陰影 `box-shadow: 0 10px 25px -4px rgba(15, 23, 42, 0.08)`
- **文字階級**：
  - 主標題：`#0f172a`（深邃曜石深藍灰，對比鮮明）
  - 次要文字與內文：`#334155` / `#475569`（沉穩易讀）
  - 輔助與時間：`#64748b`
- **七大分類專屬識別色彩**：
  - **重大事件 (Major Events)**：晶曜緋紅 `#e11d48`
  - **財金焦點 (Finance)**：翡翠青綠 `#059669`
  - **時事要聞 (Current Events)**：蔚藍寶石 `#2563eb`
  - **股市觀測 (Stock Market)**：科技霓紫 `#7c3aed`
  - **娛樂生活 (Entertainment)**：夕陽珊瑚橘 `#ea580c`
  - **會計與審計 (Accounting)**：專業青靛 `#0891b2`
  - **ESG 負面新聞 (ESG Risk)**：警示緋紅 `#dc2626`

### 4.2 排版與元件原則 (Typography & Components)
1. **字體系統**：
   - 英文與數字：`Inter`, `-apple-system`, `BlinkMacSystemFont`
   - 中文字體：`"Noto Sans TC"`, `"PingFang TC"`, `"Microsoft JhengHei"`, sans-serif
   - 數據與時間代碼：`JetBrains Mono`
2. **卡片設計 (Card Anatomy)**：
   - 每個分類至少 **5 則** 完整新聞卡片。
   - 卡片上設有：所屬分類色條、來源媒體徽章、發佈時間、閱讀時間、標題、摘要、標籤晶片、互動按鈕。
   - ESG 負面新聞卡片額外包含：「**風險等級警示燈**」（高風險/中風險/低風險）與「**E/S/G 維度標籤**」。

---

## 5. 前端頁面結構與互動功能清單 (Frontend Architecture)

`index.html` 頁面由上至下依序包含：
1. **全域頂部導航列 (Global Header)**：
   - 品牌識別：DailyPulse 綠色動態脈動光點標誌。
   - 搜尋框：支援即時輸入、全文模糊比對新聞標題、來源與標籤。
   - 功能操作區：複製今日摘要簡報 Markdown、重新整理動畫、深淺色切換。
2. **今日頭條焦點卡片 (Hero Editorial Highlight)**：
   - 挑選重大事件頭條，具備精美大卡片背景、標題、重點摘錄與快速閱讀入口。
3. **七大分類快速膠囊導覽列 (Category Navigation Pills)**：
   - 快速點擊切換篩選，並即時顯示該分類的文章數量計數（每類 5+ 則）。
4. **ESG 負面爭議與法規裁罰雷達監測看板**：
   - 統計重大高風險裁罰數、工安職災停工數、環境違規案件。
5. **七大分類專屬新聞網格 (The 7 News Grid Sections)**：
   - 重大事件、財金、時事、股市、娛樂、會計、ESG負面新聞 7 個獨立區塊。
6. **深度精華閱讀彈窗 (Article Detail Modal)**：
   - 點擊任一新聞卡片立即浮現精緻 Modal，包含新聞詳細重點摘錄（Key Takeaways）、新聞標籤、來源媒體與跳轉原文連結。
7. **頁尾 (Footer)**：
   - 規範標註、AGENTS.md 指引連結與版權聲明。

---

## 6. AI 修改或新增內容時需要遵守的規則 (Rules for AI Modifying this Project)

當任何 AI 代理人接手本專案，或使用者提出擴充需求時，**必須恪守下列原則**：

1. **不可破壞資料合約 (Zero-Breaking Schema Rule)**：
   - 新增新聞項目時，必須包含 `id`, `categoryId`, `title`, `summary`, `source`, `sourceUrl`, `publishedAt`, `readTime`, `tags`, `takeaways`。
   - 屬於 `esg_risk` 分類的新聞，必須額外具備 `riskLevel` ("high"|"medium"|"low") 與 `riskDimension` ("Environmental"|"Social"|"Governance")。
2. **各板塊數量規範**：
   - 每個板塊必須維持**至少 5 則**結構完整、內容真實的新聞。
3. **保持純靜態零編譯 (Zero Build Principle)**：
   - 嚴格禁止引入任何需要 `npm run build`、`webpack`、`vite` 等依賴編譯的打包工具。
   - 保證使用者在任何電腦上下載後，**只要雙擊 `index.html` 就能直接在瀏覽器完美運作**。
4. **語言與文字規範**：
   - 所有新聞標題、摘要與介面文案一律使用流暢、道地之**繁體中文 (台灣)**。

---

## 7. 如何將本專案上傳至 GitHub 並開啟 GitHub Pages (Deployment Guide)

使用者可以透過以下超簡易步驟將專案部署為線上可瀏覽網站：
1. 在 GitHub 建立一個新儲存庫（Repository），例如命名為 `daily-news-dashboard`。
2. 將本專案資料夾內所有檔案（`index.html`, `css/`, `js/`, `AGENTS.md`, `README.md` 等）上傳或推送至該儲存庫的主分支（`main`）。
3. 進入該 GitHub 儲存庫的 **Settings** -> **Pages**。
4. 在 **Build and deployment** 下方的 Source 選擇 **Deploy from a branch**，Branch 選擇 `main` / `/(root)`，點擊 **Save**。
5. 等待 1 分鐘，GitHub 就會產生一個專屬網址（例如 `https://your-username.github.io/daily-news-dashboard/`），任何人都可以在線上直接瀏覽！
