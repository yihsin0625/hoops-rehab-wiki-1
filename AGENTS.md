# AGENTS.md — 籃球運動防護與肌力訓練知識庫 (Hoops Rehab Wiki)

## 1. 專案目的 (Project Purpose)
本專案是一個「籃球運動員專屬的運動防護、傷後復健與專項肌力訓練知識庫」。
核心目標是將運動生物力學、關節穩定訓練與賽場防護知識結構化，讓使用者能快速查閱特定部位的訓練菜單與注意事項，並讓 AI 代理人能依據本規範持續擴充新的知識條目頁面。

## 2. 技術棧與架構規範 (Tech Stack & Architecture)
- **純靜態架構**：僅使用原生 HTML5 與 CSS3（不依賴 React、Vue 或任何需編譯的前端框架），確保可直接透過 GitHub Pages 零配置部署。
- **單一樣式來源**：所有頁面必須統一引入 `/assets/css/style.css`（在 `pages/` 目錄下的頁面需使用相對路徑 `../assets/css/style.css`），嚴禁在個別 HTML 檔案中寫行內樣式 (`style="..."`) 或獨立 `<style>` 區塊。

## 3. 目錄與檔案命名規則 (Directory & Naming Conventions)
- `index.html`：首頁，負責展示網站宗旨與所有知識條目的分類卡片索引。
- `assets/css/style.css`：全站唯一的 CSS 樣式檔。
- `pages/<topic-slug>.html`：所有單篇知識頁面皆必須放置於 `pages/` 資料夾內。
  - **命名規則**：一律使用全小寫英文與連字號（kebab-case），例如 `ankle-stability.html`、`achilles-tendon-care.html`、`bulgarian-split-squat.html`。

## 4. 網頁視覺風格與設計系統 (Design System & Visual Style)
- **色彩系統（深色運動專業風格）**：
  - 背景主色：`#0f172a`（深 slate 藍黑）
  - 卡片與區塊底色：`#1e293b`
  - 重點強調色：`#f97316`（籃球橘，用於標題重點、標籤與行動呼籲按鈕）
  - 輔助安全提示色：`#10b981`（翡翠綠，用於正確動作要領）
  - 警告風險提示色：`#ef4444`（警示紅，用於禁忌動作與就醫警訊）
  - 主要文字色：`#f8fafc`；次要說明文字：`#94a3b8`
- **排版原則**：採用卡片式模組化設計，最大閱讀寬度限制為 `900px` 置中，確保手機與桌機皆具備高可讀性。

## 5. 單一知識頁面標準結構 (Page Template Structure)
每一篇位於 `pages/` 的新頁面，必須嚴格遵守以下 HTML 區塊順序：
1. **頂部導覽列 (`<header class="navbar">`)**：左側顯示網站名稱，右側提供「← 返回知識庫首頁 (`../index.html`)」連結。
2. **文章標頭 (`<section class="article-header">`)**：包含分類標籤 (`<span class="badge">`)、文章主標題 (`<h1>`)、一句話核心摘要 (`<p class="subtitle">`) 與更新日期。
3. **核心機制與風險評估 (`<section class="card">`)**：說明該部位的常見受傷機制或訓練目的。
4. **標準訓練處方表格 (`<section class="card">`)**：使用 `<table>` 呈現，固定包含四個欄位：`動作名稱`、`目標肌群`、`組數與次數`、`執行要領`。
5. **紅綠燈安全守則 (`<div class="alert-box">`)**：明確列出「建議執行（綠燈）」與「立即停止並就醫（紅燈）」的指標。
6. **頁尾 (`<footer>`)**：版權聲明與醫療免責聲明（本知識庫僅供訓練參考，急性創傷請尋求專業物理治療師或醫師協助）。

## 6. AI 新增或修改內容的執行規則 (Rules for AI Agents)
當開發者要求「新增一篇關於 [某主題] 的頁面」時，AI 必須依序執行以下動作，缺一不可：
1. **檢查命名**：依據第 3 條規則，將主題轉換為英文 kebab-case 檔名，建立 `pages/<slug>.html`。
2. **套用結構**：完全遵循第 5 條的 6 個 HTML 區塊順序與 CSS Class 名稱（`.navbar`, `.article-header`, `.badge`, `.card`, `.alert-box`），不隨意更改結構。
3. **同步更新首頁索引**：建立新頁面後，**必須同步修改根目錄的 `index.html`**，在對應的分類網格 (`<div class="card-grid">`) 中新增一張指向該新頁面的連結卡片（包含標題、標籤與 30 字內簡介），確保使用者能從首頁點擊進入。
4. **語氣與專業度**：內容需使用繁體中文，語氣客觀、精準，具運動科學與實戰訓練邏輯，避免空泛形容詞。