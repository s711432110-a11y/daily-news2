# CLAUDE.md - DailyPulse 指引與核心開發規則

> 本檔案專門為 Claude Code 與相容代理人設計。詳細架構規範請參閱同目錄下的 [AGENTS.md](file:///c:/Users/User/Desktop/daily_news/AGENTS.md)。

## 專案核心目標
`DailyPulse` 是一個純靜態、零後端依賴、開箱即用的每日新聞精緻儀表板，全面採**現代典雅淺色雜誌風格**（Light Editorial Aesthetic），涵蓋**七大板塊**（每板塊至少 5 則重點新聞）：
1. **重大事件 (Major Events)**：跨領域重大突發、全球高峰會與科技里程碑
2. **財金焦點 (Finance)**：總體經濟、通膨走勢、央行政策與匯率
3. **時事要聞 (Current Events)**：公共政策、國會法案審查與民生新制
4. **股市觀測 (Stock Market)**：台股半導體、AI概念股、美股四大指數與法說動態
5. **娛樂生活 (Entertainment)**：金馬獎、大巨蛋演唱會經濟與串流影劇
6. **會計與審計 (Accounting)**：審計準則公報、IFRS S1/S2 永續確信與 CFC 反避稅查核
7. **ESG 負面新聞 (ESG Risk & Controversies)**：環保排污開罰、重大職災停工與內線交易弊端監警

## 快速預覽方式
無需安裝任何 Python 或 Node.js，直接在檔案總管中雙擊 `index.html` 即可在瀏覽器完整開啟。亦可使用任何簡易靜態伺服器開啟。

## 檔案結構
- `index.html`: 主儀表板頁面（HTML5 結構）
- `css/style.css`: 現代典雅淺色設計系統（精緻卡片邊框、柔和立體陰影、分類專屬色彩）
- `js/app.js`: 前端新聞資料集（7 大板塊 × 5 則以上）、搜尋、分類切換、摘要彈窗與書籤邏輯
- `AGENTS.md`: 完整的 AI 開發架構指南與擴充守則
- `README.md`: 專案介紹與 GitHub Pages 免費部署說明

## AI 開發守則
1. **保持純靜態零編譯 (Zero Build Principle)**：不可引入打包工具或需要後端伺服器的依賴，確保雙擊 `index.html` 即可運作。
2. **不可破壞資料結構**：嚴格遵守 `AGENTS.md` 第 3 節的 JSON Schema，每個板塊維持至少 5 則新聞。
3. **設計原則**：現代典雅淺色風格（純白卡片、冷壓灰底、鮮明清晰文字與細緻陰影）。
