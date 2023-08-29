# 後台excel表單，可快速修改選票狀態與選項，目前投票結果也暫時要來這邊查看

https://docs.google.com/spreadsheets/d/1CYcfKpTWT7D5FIu3ksjspVDMcs4ZS49ofxEE5pn16IU/edit?usp=sharing

# 服務連結網址

[網址1](https://google-vote-001.vercel.app/)
[網址2](https://google-vote-001-git-main-randjtw.vercel.app/)

# 選票相關API

雖然直接修改excel表單即可達成任何操作，但是有些操作還是做成自動化比較方便

## 計算目前選票數量 (https://google-vote-001.vercel.app/tickets/serial/count)

經由程式計算序號數量，預計要給開票功能使用

## 計算目前已使用選票數量 (https://google-vote-001.vercel.app/tickets/used/count)

經由程式計算已使用序號數量，預計要給開票功能使用

## 檢查選票序號是否重複 (https://google-vote-001.vercel.app/tickets/check/repeat)

序號應該是要不重複的，但是以程式產生或是人工輸入，難免會出現重複

## 檢查特定選票序號是否已使用 (https://google-vote-001.vercel.app/tickets/check/used/輸入欲查詢序號)

輸入序號檢查是否已使用

## 新增選票 (https://google-vote-001.vercel.app/tickets/insert/輸入欲新增之數量)

輸入數量新增選票

## 驗證新增選票 (https://google-vote-001.vercel.app/輸入序號)

驗證選票是否存在，新增序號後使用，點擊按鈕進入

## 開票頁面1 (https://google-vote-001.vercel.app/stats/step1)

顯示目前應投票數與未投票數，以及未投序號，須配合上方選票統計功能使用

## 開票頁面2 (https://google-vote-001.vercel.app/stats/result1)

單選議題開票圖表畫面

## 開票頁面3 (https://google-vote-001.vercel.app/stats/result2)

複選議題開票圖表畫面

## 開票頁面4 (https://google-vote-001.vercel.app/stats/result3)

委員選舉開票圖表畫面

# 如何製作選票QR code

- 服務網址 + "/" + 選票序號
-- 假設選票序號為"123456"，選票網址即為https://google-vote-001.vercel.app/123456
- 將網址以QR code產生工具製作二維碼，下面是建議的工具網站
-- [點我開啟網站](https://qr.ioi.tw/zh/)

# 報到、領票與管委會委員選舉流程
> [用這個網站讀取並顯示Mark Down格式](https://stackedit.io/app) | [線上MD使用簡介](https://claire-chang.com/2019/10/10/%E5%A5%BD%E7%94%A8%E7%9A%84markdown%E7%B7%9A%E4%B8%8A%E7%B7%A8%E8%BC%AF%E5%B7%A5%E5%85%B7-stackedit/)

``` mermaid
graph TD
領票前設定投票模式為非區權人選舉-->區權人領票
設定投票模式為非區權人選舉-->宣佈與輸入投票開始時間
清除領票後亂投的票-->重複流程2((進行管委選舉投票))
區權人簽到-->重複流程1((工作人員登記流水號))
區權人領票-->重複流程1((工作人員登記流水號))-->區權人領票
重複流程1((工作人員登記流水號))-->報到完成-->作廢選票統計-->執行廢票計算API-->宣佈與輸入投票開始時間-->重複流程2((進行管委選舉投票))-->開啟投票進行中網頁
刷新投票網頁-->重複流程2((進行管委選舉投票))-->刷新投票進行中網頁-->未投票序號數量清零-->重複流程3((投票狀況排除))-->未投票序號數量清零
未投票序號數量清零-->宣佈與輸入投票結束時間-->確認未出現時間錯誤之投票內容-->開啟統計圖表頁面-->投票結果另存新檔
```

# 議題討論與表決流程
``` mermaid
graph TD
投票模式維持區權人選舉-->進行議題投票前宣導關閉之前投票的網頁-->選票已使用改為未使用-->議題選項修改-->切換投票模式為議題選舉-->宣佈與輸入投票開始時間-->清除亂投的票-->重複流程1((進行議題投票))-->開啟投票進行中網頁
刷新投票進行中網頁-->重複流程1((進行議題投票))-->刷新投票進行中網頁-->未投票序號數量清零-->投票狀況排除-->未投票序號數量清零-->宣佈與輸入投票結束時間-->確認未出現時間錯誤之投票內容-->開啟統計圖表頁面-->投票結果另存新檔
```