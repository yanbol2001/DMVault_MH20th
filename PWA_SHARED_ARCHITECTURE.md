# DMVault 共用 PWA 基礎架構

本版 MH20th 已拆成「作品設定」與「共用引擎」兩層：

- `pwa/project-config.js`：作品名稱、版本、GA4 ID、主題色。
- `pwa/dmvault-pwa.js`：Service Worker 註冊、更新提示、Android/桌面安裝提示、iOS 加入主畫面說明、GA4 共用事件。
- `pwa/dmvault-pwa.css`：安裝與更新提示 UI。
- `service-worker.js`：核心檔預快取、圖片與其他資源使用時快取、HTML 網路優先。
- `manifest.webmanifest` 與 `icons/`：可安裝資訊與跨平台圖示。

## 套用到 Pendulum COLOR／哥吉拉

1. 複製 `pwa/` 與提示樣式。
2. 修改 `project-config.js` 的 projectId、projectName、version、analyticsId。
3. 依作品調整 manifest 名稱、圖示、起始頁與捷徑。
4. 依網站實際入口調整 service-worker.js 的 CORE 清單。
5. 每頁設定 `data-dmvault-root`，並引用共用 CSS/JS。

GA4 目前會送出：一般 page_view、dmvault_launch、navigation_click、outbound_click、pwa_installed、pwa_install_prompt_result。培育紀錄與「已養過」資料不會上傳。
