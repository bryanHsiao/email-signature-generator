# Email 簽名檔產生器

> 線上工具：**https://bryanhsiao.github.io/email-signature-generator/**

一個單頁 HTML 工具，即時編輯、預覽並一鍵匯出相容各大 Email 客戶端的簽名檔。

## 功能特色

- **即時預覽** — 表單輸入即時反映在右側模擬信件畫面
- **一鍵複製 HTML** — 簽名採用 `table` 排版 + inline style，可直接貼入 Outlook、Gmail、Apple Mail、HCL Notes 的簽名設定
- **下載 HTML 檔案** — 匯出完整 `signature.html`，可在 HCL Notes 選擇此檔案作為簽名
- **下載圖片** — 使用 html2canvas 將簽名截圖為 `signature.png`（適合 Notes Richtext 嵌入圖片方式）
- **複製純文字** — 備用純文字格式
- **4 種配色方案** — 科技藍、活力橘、優雅紫、清新綠
- **Logo 支援** — 上傳本機圖片（自動轉 Base64）、填入公開圖片網址，或使用預設 Logo
- **無需伺服器** — 直接開啟 `index.html` 即可使用，或透過 GitHub Pages 線上存取
- **RWD 響應式** — 支援桌機與行動裝置

## 線上使用

直接開啟網址，無需安裝：

```
https://bryanhsiao.github.io/email-signature-generator/
```

## 本機使用

下載或 clone 專案後，用瀏覽器開啟 `index.html`：

```bash
git clone https://github.com/bryanHsiao/email-signature-generator.git
cd email-signature-generator
# 直接用瀏覽器開啟 index.html
```

## 簽名欄位

| 欄位 | 說明 |
|------|------|
| 英文姓名 | 顯示於簽名標題（大字） |
| 中文姓名 | 緊接英文名旁 |
| 公司英文名 | Header 橫幅及內文顯示 |
| 公司中文名 | Header 橫幅及內文顯示 |
| Tie-Line | 內線電話 |
| Outside | 手機號碼 |
| Email | 電子郵件（可點擊） |
| 公司網站 | 超連結（可點擊） |
| 郵寄地址 | 公司地址 |
| 地區 | 城市與國家 |

## Logo 使用建議

| 方式 | 跨客戶端 | 離線可見 | 適用情境 |
|------|---------|---------|---------|
| **公開 URL** | ✅ 好 | ❌ 需連網 | 一般 HTML 簽名 |
| **上傳圖片（Base64）** | ⚠️ Outlook 可能擋 | ✅ | HCL Notes 本機 .html 簽名檔 |
| **下載圖片後嵌入** | ✅ 最佳 | ✅ | HCL Notes Richtext 格式簽名 |

> **HCL Notes 最佳做法：** 下載 `signature.png` → 在 Notes Richtext 簽名中以「插入圖片檔案」方式嵌入，圖片會以 CID 方式隨信傳送，收件方不需連網即可看到完整簽名。

## Email 客戶端相容性

產生的簽名 HTML 採用以下方式確保相容性：

- `<table>` 佈局（不使用 flexbox / grid）
- 全部 inline style，無外部 CSS
- `bgcolor` 屬性 + `background-color` 雙保險
- Web-safe 字體（Arial / Helvetica）
- `<img>` 加上 `width`、`height`、`border="0"` 屬性
- 全域 `width="100%"` 確保 Header 滿版

## 專案結構

```
email-signature-generator/
├── index.html   # 主程式（全部內嵌，單一檔案）
├── .gitignore
└── README.md
```

## 預設資訊

工具預設填入崇太科技實業有限公司 Bryan Hsiao 的聯絡資訊，可修改成任何人的資料。
