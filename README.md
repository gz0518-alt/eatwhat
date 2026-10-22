# 今天吃什麼（EatWhat）

## 在 Mac 上測試
雙擊 `啟動測試.command`，瀏覽器會自動打開 App。
（第一次若被 macOS 擋下：在檔案上按右鍵 →「打開」。）
用完關掉終端機視窗即可。

## 放到 iPhone 上用（GitHub Pages，免費）
iPhone 要抓目前位置，網頁必須是 HTTPS，所以要放到網路上：

1. 到 github.com 註冊／登入，右上角「＋」→ New repository，名稱填 `eatwhat`，選 Public，建立
2. 在新的 repo 頁面點「uploading an existing file」，把這個資料夾裡的檔案全部拖進去
   （`index.html`、`manifest.json`、`sw.js`、三個 `icon-*.png`），按 Commit changes
3. repo 上方 Settings → 左邊 Pages → Branch 選 `main`、資料夾 `/ (root)` → Save
4. 等 1–2 分鐘，網址會是 `https://你的帳號.github.io/eatwhat/`
5. iPhone 用 Safari 打開這個網址 → 分享按鈕 →「加入主畫面」

之後主畫面就有「吃什麼」的圖示，打開就是全螢幕 App。

## 使用方式
- 上方切換轉盤（國家／形式／中西式），「＋ 新轉盤」可以自己建
- 按「轉！」或點轉盤開始
- 結果出來後：
  - 🚶 走路找／🚗 開車找 → 打開 Google Maps 搜尋附近
  - 不想吃，再抽一次 → 把這個選項排除，自動再轉
- 排除的選項當天有效，隔天自動恢復；也可以按「重置」
- ⚙️ 設定：改轉盤名稱、新增／刪除選項、調整走路與開車的搜尋範圍

## 資料
所有轉盤設定都存在手機本機（Safari 的網站資料），不需要帳號。
清除 Safari 網站資料會讓自訂轉盤回到預設。

## 之後可升級
接上 Google Places API 後，可以在 App 裡直接顯示附近 3 間餐廳的評分與評論。

## Google API 金鑰（推薦 3 間、精準距離、預算篩選）
1. 到 https://console.cloud.google.com 建立專案（名稱例如 eatwhat）
2. 左上選單 → 帳單 → 連結帳單帳戶（需要信用卡）
3. 「API 和服務」→「程式庫」，啟用：**Places API (New)**、**Routes API**
4. 「API 和服務」→「憑證」→ 建立憑證 → API 金鑰，然後編輯這把金鑰：
   - 應用程式限制：網站 → 加入 `https://gz0518-alt.github.io/*` 和 `http://localhost:8765/*`
   - API 限制：只勾 Places API (New)、Routes API
5. 把金鑰貼到 App 的 ⚙️ 設定 →「Google API 金鑰」
金鑰只存在手機上，不會上傳到 GitHub。App 每天最多搜尋 30 次。
