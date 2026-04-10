# Email 簽名檔產生器

一個單頁 HTML 工具，讓您即時編輯、預覽並一鍵複製相容各大 Email 客戶端的簽名 HTML。

## 功能特色

- **即時預覽** — 表單輸入即時反映在右側模擬信件畫面
- **一鍵複製 HTML** — 產生的簽名採用 `table` 排版 + inline style，可直接貼入 Outlook、Gmail、Apple Mail 的簽名設定
- **複製純文字** — 同時提供純文字版本
- **4 種配色方案** — 科技藍、活力橘、優雅紫、清新綠，隨時切換
- **Logo 支援** — 上傳本地圖片（自動轉 Base64）、輸入圖片網址，或使用自動生成的預設 Logo
- **無需伺服器** — 直接用瀏覽器開啟 `index.html` 即可使用
- **RWD 響應式** — 支援桌機與行動裝置

## 快速開始

直接用瀏覽器開啟 `index.html`，無需安裝任何套件。

```
index.html  ←  雙擊或拖曳到瀏覽器即可
```

## 簽名欄位

| 欄位 | 說明 |
|------|------|
| 英文姓名 | 顯示於簽名標題（大字） |
| 中文姓名 | 顯示於英文名旁（小字） |
| 公司英文名 | 顯示於分隔線下方 |
| 公司中文名 | 顯示於英文名下方（灰字） |
| Tie-Line | 內線電話 |
| Outside | 手機號碼 |
| Email | 電子郵件（可點擊） |
| 公司網站 | 超連結（可點擊） |
| 郵寄地址 | 公司地址 |
| 地區 | 城市與國家 |

## Email 客戶端相容性

產生的簽名 HTML 採用以下方式確保相容性：

- 使用 `<table>` 佈局（不使用 flexbox / grid）
- 所有樣式使用 inline style
- 不使用 CSS gradient 作為背景（改用 `bgcolor` 屬性 + `background-color`）
- 使用 Web-safe 字體（Arial / Helvetica）
- 圖片加上 `width`、`height`、`border="0"` 屬性

## 專案結構

```
20260409-HTML_signature/
├── index.html   # 主程式（全部內嵌，單一檔案）
├── .gitignore
└── README.md
```

## 預設資訊

工具預設填入崇太科技實業有限公司 Bryan Hsiao 的聯絡資訊，可直接修改成任何人的資料。
