# Email 簽名檔產生器

> 線上工具：**https://bryanhsiao.github.io/email-signature-generator/**

一個單頁 HTML 工具，所見即所得直接在預覽畫面編輯，即時產生相容各大 Email 客戶端的簽名檔。

---

## 功能特色

### ✏️ 所見即所得編輯
- 直接點擊右側預覽簽名中的任意文字即可編輯，修改立即反映
- 無需切換表單，所有欄位皆可在預覽畫面中直接修改

### 🎨 配色方案
- 內建 **3 種主題**：科技藍、深色模式、午夜靛
- **自訂配色**：點擊「自訂」按鈕開啟系統色盤，自由選取主色，次要色自動推算

### 🖼️ Logo 支援
- 上傳本機圖片（自動轉 Base64 嵌入）
- 填入公開圖片網址
- 一鍵還原預設 Logo

### 🍎 外觀設定
- **姓名顏色**：自訂姓名文字顏色
- **英文 / 中文字體**：各自獨立選擇，英文提供 Google Fonts 草書、優雅等多種風格，中文提供楷體、黑體、明體等系統字體
- **右上圓圈裝飾**：macOS 風格三色圓點，可開關切換

### 📤 多種匯出格式

| 按鈕 | 說明 | 適用場景 |
|------|------|---------|
| **🗺 圖片含連結** | 圖片 + Image Map，email / 網址可點擊 | 通用，各類郵件客戶端皆適用 |
| **🖼 下載圖片** | 純 PNG，1142px 固定寬度 | 需嵌入圖片的場景 |
| **複製 HTML** | `table` 排版 + inline style HTML | Outlook / Gmail / Apple Mail 原生簽名設定 |
| **複製純文字** | 備用純文字格式 | 無 HTML 支援的場合 |
| **下載 HTML** | 匯出完整 `signature.html` | 進階使用 |

### 🌐 無需伺服器
- 直接開啟 `index.html` 即可使用，或透過 GitHub Pages 線上存取
- 全部邏輯內嵌於單一 HTML 檔案，無外部依賴

---

## 圖片含連結（Image Map）技術說明

純圖片簽名無法加入可點擊連結，而各家郵件客戶端對 HTML 簽名的支援程度不一（尤其 HCL Notes 對複雜 CSS 的渲染較差）。「圖片含連結」採用以下思路解決這個問題：

### 思路

```
預覽 DOM → 計算元素位置 → 對應到圖片像素座標 → 寫入 Image Map
```

1. **從預覽 DOM 取得精確座標**  
   簽名已在預覽畫面正確渲染，直接對 `[data-field="email"]`、`[data-field="website"]` 元素呼叫 `getBoundingClientRect()`，取得相對於預覽容器的像素位置。這比事後猜測位置更準確。

2. **乘上 scale 換算到輸出圖片座標**  
   html2canvas 截圖時使用 `scale = 1142 / offsetWidth`，讓輸出寬度固定為 1142px。DOM 座標乘上同一個 scale，就能精確對應到圖片上的像素位置。

3. **產生 `<map>` + `<area>`**  
   計算好的座標寫入 HTML Image Map：
   - email 區域 → `href="mailto:..."`
   - 網址區域 → `href="https://..." target="_blank"`

4. **圖片以 Base64 嵌入**  
   整個 `signature-linked.html` 自包含，不依賴外部檔案，可直接作為簽名設定載入。

### 輸出格式

```html
<img src="data:image/png;base64,..." usemap="#sigmap" width="1142" height="...">
<map name="sigmap">
  <area shape="rect" coords="x1,y1,x2,y2" href="mailto:user@domain.com" alt="Email">
  <area shape="rect" coords="x1,y1,x2,y2" href="https://website.com" target="_blank" alt="Website">
</map>
```

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
| 公司電話 | 內線電話 |
| 行動電話 | 手機號碼 |
| 電子郵件 | 可點擊連結 |
| 公司網站 | 可點擊超連結 |
| 地址 | 公司地址 |
| 地區 | 城市與國家 |

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
