# VOCABCLASH | 大廳字標與獨立 App 版

發布識別：`vc-app-r2`。此版以最新的 Neon 大廳移除大型 Logo 版為基礎，不是最早的原始遊戲。

## 這次的調整

- 大廳主內容恢復 VOCABCLASH 字樣，沒有大型圖片 Logo。頁首小 Logo 保留。
- 主標「把背單字，變成一場遊戲。」、現有配色與操作流程不變。
- 對照 ARCO-v2.5.0-Logo-Ready，保留 `display: standalone` 與 `id/start_url/scope: ./`；加強安全邊界與安裝提示。上版已有核心獨立視窗宣告，不是這次才從零加入。
- 圖示檔改用 r2 檔名，圖片內容不重畫。提供 ICO、PNG、Apple-touch 與 maskable 尺寸。
- 設定內新增可展開的「安裝成 App」，顯示當前是獨立視窗或瀏覽器分頁。只在瀏覽器提供安裝事件時顯示安裝按鍵。

## 預覽與正式上架的差別

`VocabClash-App-Preview.html` 是可直接用瀏覽器開啟的完整遊戲預覽。圖片已內嵌，雙人連線仍需網路。本機預覽不能當成已發布的 App 安裝入口。

正式上架請使用 `VocabClash-App-Ready.zip` 內的 `index.html`，並一起上傳其他資源，不要只把預覽版改名上傳。

## GitHub Pages 更新

1. 先從原遊戲或舊主畫面 App 的單字庫匯出備份，私人備份不要放到 GitHub。
2. 解壓縮後將內容放到原本的 Pages 發布位置，覆蓋同名檔案。不要只上傳 ZIP，也不要多包一層資料夾。
3. 保留 `icons/`、`site.webmanifest`、`favicon.ico`、`apple-touch-icon.png`、`.nojekyll` 與授權聲明。不要刪除原本的 `CNAME`、`README.md`、`.github/` 或自訂設定。
4. 發布成功後使用原本的 HTTPS 遊戲網址。雙方重新載入並重新開房。
5. 可先打開 `logo-check.html`按「開始檢查」。檢查完後先「返回遊戲」再安裝，不要把檢查頁加入主畫面。

```text
index.html
site.webmanifest
favicon.ico
apple-touch-icon.png
icons/                 # r2 PNG / ICO files
logo-check.html
.nojekyll
THIRD_PARTY_NOTICES.txt
APP-SETUP.md
APP-TEST-REPORT.md
APP-CHECKS.json
```

## iPhone / iPad 獨立 App

使用 Safari 直接打開正式遊戲網址，選「分享」→「加入主畫面」；若出現「打開為網頁 App」，請開啟，再按「加入」。之後從手機或平板主畫面的圖示啟動。[1][2]

不要用 GitHub 程式碼頁、Raw 連結、本機 HTML、LINE 內嵌瀏覽器或 Google Sites 外層頁面來安裝這個遊戲。先改用 Safari 開啟直接遊戲網址。

安裝成功後從圖示啟動，才會使用 standalone 視窗。從 Safari 或訊息裡點一般網址，仍可能用原本的分頁開啟。網站不能強制把一般分頁的瀏覽器介面移除。[3]

## Android 與電腦

Android 使用 Chrome 選單中的安裝選項；有「安裝」與「捷徑」區別時，選擇安裝。電腦使用支援的 Chrome / Edge 安裝功能；Mac Safari 可用「加入 Dock」。安裝入口依裝置與瀏覽器版本而異。[3]

## 舊圖示或舊捷徑

先從舊圖示開啟遊戲並匯出備份，再移除舊捷徑，從更新後的正式網址重新加入。切換開啟方式後若沒有看到原資料，請匯入備份。不要為了更新圖示就清除所有網站資料。[5]

新圖示使用新檔名以避免沿用舊網址快取，但不能強制已安裝的所有捷徑立刻更新。舊 r1 檔案可留在原儲存庫供舊版載入，新版使用 r2。

## 保留的功能與限制

原有 14 段 JavaScript 逐段比對完全一致。題庫、對戰、計分、連線、教學、發音、收藏、錯題與統計格式都沒有更動。只新增一段安裝提示程式。

沒有加入 Service Worker、清除快取程式、廣告或追蹤。安裝圖示不等於雲端同步、離線對戰或永久資料備份。關閉房主 App 後也不保證恢復原對戰。

已完成本機資源、尺寸、排版、教學與 AI 操作檢查。尚未在你的正式網站、實體 iPhone / iPad / Android 或真正桌面安裝視窗實測，不宣稱所有裝置都已驗證。詳見 `APP-TEST-REPORT.md`。

## 官方參考

[1] Apple iPhone: https://support.apple.com/zh-tw/guide/iphone/iph42ab2f3a7/ios
[2] Apple iPad: https://support.apple.com/zh-tw/guide/ipad/ipad8f1f7a29/ipados
[3] MDN standalone: https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/How_to/Create_a_standalone_app
[4] MDN icons: https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest/Reference/icons
[5] MDN storage: https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria
