# Email 簽名檔產生器

> 線上工具：**https://bryanhsiao.github.io/email-signature-generator/**

一個單頁 HTML 工具，所見即所得直接在預覽畫面編輯，即時產生相容各大 Email 客戶端的簽名檔。

---

## 功能特色

### ✏️ 所見即所得編輯
- 直接點擊右側預覽簽名中的任意文字即可編輯，修改立即反映
- 無需切換表單，所有欄位皆可在預覽畫面中直接修改

### 🎨 配色方案
- 內建 **7 種主題**：科技藍、活力橘、優雅紫、清新綠、深色模式、珊瑚紅、午夜靛
- **自訂配色**：點擊「自訂」按鈕開啟系統色盤，自由選取主色，次要色自動推算

### 🖼️ Logo 支援
- 上傳本機圖片（自動轉 Base64 嵌入）
- 填入公開圖片網址
- 一鍵還原預設 Logo（崇太科技 CTIlogo）

### 🍎 外觀設定
- **姓名顏色**：自訂姓名文字顏色
- **右上圓圈裝飾**：macOS 風格三色圓點，可開關切換（顯示 / 隱藏）

### 📤 多種匯出格式
| 按鈕 | 說明 |
|------|------|
| **複製 HTML** | 複製 `table` 排版 + inline style HTML，可直接貼入 Outlook、Gmail、Apple Mail、HCL Notes |
| **複製純文字** | 備用純文字格式 |
| **下載 HTML** | 匯出完整 `signature.html`，可在 HCL Notes 選擇此檔案作為簽名 |

### 🌐 無需伺服器
- 直接開啟 `index.html` 即可使用，或透過 GitHub Pages 線上存取
- 全部邏輯內嵌於單一 HTML 檔案，無外部依賴

---

## 線上使用

```
https://bryanhsiao.github.io/email-signature-generator/
```

## 本機使用

```bash
git clone https://github.com/bryanHsiao/email-signature-generator.git
cd email-signature-generator
# 直接用瀏覽器開啟 index.html
```

---

## 簽名欄位說明

| 欄位 | 說明 |
|------|------|
| 英文姓名 | 顯示於簽名主體（粗體大字） |
| 中文姓名 | 緊接英文名旁 |
| 公司英文名 | Header 橫幅及內文 |
| 公司中文名 | Header 橫幅及內文 |
| 公司電話 | Tie-Line 內線 |
| 行動電話 | 手機號碼 |
| 電子郵件 | 可點擊連結 |
| 公司網站 | 可點擊超連結 |
| 地址 | 公司地址 |
| 地區 | 城市與國家 |

---

## Logo 使用建議

| 方式 | 跨客戶端 | 離線可見 | 適用情境 |
|------|---------|---------|---------|
| **公開 URL** | ✅ 佳 | ❌ 需連網 | 一般 HTML 簽名 |
| **上傳圖片（Base64 嵌入）** | ⚠️ Outlook 可能擋 | ✅ | HCL Notes 本機 .html 簽名檔 |

> **HCL Notes 建議做法：** 使用「複製 HTML」貼入 Notes 簽名設定，或下載 `signature.html` 後在 Notes 中以「HTML 檔案」方式載入。

---

## Email 客戶端相容性

產生的簽名 HTML 採用下列方式確保相容性：

- `<table>` 佈局（不使用 flexbox / grid）
- 全部 inline style，無外部 CSS
- `bgcolor` 屬性 + `background-color` 雙保險
- Web-safe 字體（Arial / Helvetica）
- `<img>` 附上 `width`、`height`、`border="0"` 屬性

---

## 專案結構

```
email-signature-generator/
├── index.html   # 主程式（全部內嵌，單一檔案）
├── .gitignore
└── README.md
```

---

## 預設資訊

工具預設填入崇太科技實業有限公司 Bryan Hsiao 的聯絡資訊，可直接在預覽畫面點擊修改成任何人的資料。
