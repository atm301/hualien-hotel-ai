# 花蓮觀光旅宿 AI 營運實作專班 Day 1

TISSA 115 年 AI 實作專班（觀光旅宿業）學員互動站。
講師：何佳勳（小圭）· 圭話行銷股份有限公司
時間：2026/10/27（二）09:00 到 16:00　地點：F HOTEL 花蓮站前館 吉祥廳

## 網址

| 頁面 | 網址 | 用途 |
|---|---|---|
| 學員站 | https://atm301.github.io/hualien-hotel-ai/ | 上課用，手機開 |
| 講師後台 | https://atm301.github.io/hualien-hotel-ai/admin.html | 自評統計、交件、計分、CSV |
| 投影頁 | https://atm301.github.io/hualien-hotel-ai/board.html | 計分榜、暖身牆、自評落點 |

## 這一站的重點

- **AI 落點自評表（10 題）**：線上作答、自動計分與階段判定，講師後台看得到全班落點與每一題的比例，直接決定當天示範深度。
- **一週工作盤點計算機**：學員填自己的時數，算出一週總時數與 AI 可分擔上限，並建議先改善哪一條流程。
- **R-T-C-F 組裝器、品牌口吻指令卡、底稿事實清單**：三個填寫器都會組成可直接複製的提示詞，指令卡會自動帶進底稿提示詞。
- **LINE 訊息成本試算**：11/1 新制，輕用量與中用量超出免費額度會警告「發不出去」。
- **練習素材包**：示範民宿「山海小棧」的 20 則客服對話、30 則旅客評論與店家基本資料，沒有自家資料的學員可直接練習，也是 Day 2 評論分析的備援素材。
- **11 組提示詞**：對應簡報四個模組，一鍵複製。
- **34 支 ECom 工具**：依模組分組，全部驗證過 HTTP 200，外連自動帶 UTM。

## 兩天共用同一個網址

分數要跨兩天累計，所以 `COHORT` 固定為 `hualien-1027`，不是用日期自動分梯。
Day 2 的內容之後直接加分頁進來，學員不用換網址，報到資料與分數都會延續。

## 資料表

共用 Supabase `dpglkagtzdwiovzbtase`：

- `lw_line_students`：報到資料、互動題答案、自評表、三個填寫器的內容（存在 `quiz` jsonb）
- `lw_workshop_submissions`：交件與暖身牆。`task` 值為 `m1`／`m2`／`m3`／`m4`／`hw`／`warm`／`extra`
- `lw_workshop_scores`：講師手動加分
- Storage bucket `lw-workshop`：上傳的圖片

## 課後

1. 後台各分頁都有「⬇️ 匯出 CSV」，先匯出再清資料。
2. 清資料要用 Supabase Management API（anon key 沒有 DELETE 權限），條件 `course='hualien-hotel-ai'`。
3. 交件與暖身牆對所有訪客公開，課後建議清掉。

## 開發

單一 `index.html`（約 186 KB，含 CSS 與 JS），無建置流程。改完直接 push，GitHub Pages 幾分鐘後生效。

正解：互動題 1 到 8 依序為 B、B、A、C、B、B、C、A。
