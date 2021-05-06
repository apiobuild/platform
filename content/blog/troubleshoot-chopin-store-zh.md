---
title: "Chopin 網路商店設定常見問題"
image: /images/blog/faqs.png
date: 2020-08-06
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation","教學", "網路開店","常見問題"]
---

設定 [Chopin](https://telescope.apiobuild.com/app/chopin) 網路商店的過程中，如果碰到一些小難題、看到錯誤訊息或是哭哭的派大星，不要緊張，可以參考[新手常見錯誤](#checklist)自行除錯看看！

常見問題包括[圖片顯示](#圖片)、[商品目錄和訂單 google sheet](#商品目錄和訂單)、[付款方式](#付款方式)等等，也收錄了[其他小問題](#其他問題)。

如果還是無法解決的話，歡迎直接聯絡我們！可以<a href="mailto:apiobuild@gmail.com">寫信</a>或是使用 [Facebook 訊息](https://m.me/apiobuild)!

<img src="/images/blog/chopin-error.png" class="post-img">

<!--more-->

🛍️ [還沒有 Chopin Store? 跟著這篇教學建立商店](https://apiobuild.com/blog/how-to-create-web-store-with-apio-ch/)

🛍️ [看這裡了解 Chopin 各項設定](https://apiobuild.com/blog/how-to-configure-chopin-store-zh/)

## Checklist

建議你先檢查以下新手常見錯誤，一一排除之後可能問題就解決了喔！

### Google Sheet 資料

- 檢查商品目錄 google sheet 資料，每列之間不得穿插空白列
- 商品目錄 google sheet 中，每個產品的 `name` 欄不得是空白，不能重複，不能出現英文數字外的字符，不能有空格。
- 訂單 google sheet 中，`order_number` 必須是第一欄，且不能隱藏。
- 檢查所有的圖片連結是否為 [direct links](#為什麼圖片無法顯示)，可以貼到網址列試試。
- 是否動到從教學複製而來的標題列呢？不要更動兩個 google sheets 的標題列文字，修改格式或是調動位置是沒問題的。

### Chopin

- 點擊設定按鈕 (<i class="fas fa-cog"></i>) 進入 [Telescope 帳戶](https://telescope.apiobuild.com/settings). 檢查登入 Telescope 和 Chopin 開店的帳號是不是相同。可以試試完全登出後，再重新以 **google 帳號** (在彈出視窗點選 `Sign in with Google`) 登入。
- 檢查你是否跟著[Chopin Flow 步驟](https://telescope.apiobuild.com/flow/chopin-stores)建立**兩個** google sheet，也都按照流程完成貼上標題列、分享權限給 Waitress 帳號、授權。

### 瀏覽器

- 封鎖彈出視窗的功能有時候會影響 google sheet 授權過程. 可以取消此功能再重複[步驟2](https://apiobuild.com/blog/how-to-create-web-store-with-apio/#step-2-新增商品目錄-google-sheet)試試。

<br>

## 圖片

### 如何取得手邊圖片的網址呢？

🙋 可以使用圖片網址生成服務，像是 [Imgbb](https://zh-tw.imgbb.com/) 或 [img.onl](https://img.onl/) 。成功上傳圖片成功後，會得到一串 **image url** 或是 **direct link** (請參考下圖)

<img src="/images/blog/faq-image-link.png" class="post-img">

### 為什麼圖片無法顯示？

🙋 檢查是否貼上完整的圖片網址，還是只是一個外部網頁連結。可以把連結放到瀏覽器網址列試試，如果只有顯示圖片，那就是正確可使用的圖片網址

🙋 把圖片換到[圖片網址生成服務](#如何取得手邊圖片的網址呢)，再試試看。Facebook 或是 Google Drive/Dropbox 等圖片連結，會因為存取次數超過平均值或是過了一段時間而失效。

### 如何從網站或是Facebook獲得圖片網址？

🙋 右鍵點擊圖片 > 選取 `複製圖片網址` (`Copy Image Address`)。但我們仍建議使用上述[圖片網址生成服務](#如何取得手邊圖片的網址呢)，可確保連結不會失效。

### 為什麼圖片載入速度很慢？

🙋 有可能是圖片檔案太大，建議將圖片檔案大小控制在500kb以下，可以使用 [TinyPNG](https://tinypng.com/) 縮減檔案大小。

<br>

## 商品目錄和訂單

### 如何開啟新訂單自動通知

🙋在商品目錄的 google sheet 中，按一下頂端的`工具` > `通知規則`，選取您要接收通知的時間點，[參考教學](https://support.google.com/docs/answer/91588?co=GENIE.Platform%3DDesktop&hl=zh-Hant)

### 可以移動、新增或隱藏訂單 google sheet 中的欄位嗎？

🙋添加、隱藏欄位或是移動標題列中的欄位排序都不會影響資料的寫入，也可以自由變更欄位顯示顏色！注意：`order_number` 一定要是第一個欄位，不能移動或隱藏。建議在網站流量小的時候操作。

### 不想看到過去的訂單或是不會再製造的產品怎麼辦？

🙋不建議刪掉任何資料，這些都是之後分析顧客喜好或是成本收益的寶貴資料。可以選擇隱藏過去訂單那幾列 (選取列 > 右鍵 > 隱藏列) 或是隱藏某幾項產品 ([使用商品目錄中的 hide 儲存格](https://apiobuild.com/blog/how-to-configure-chopin-store-zh/#更新商品目錄))。注意：`order_number` 一定要是第一個欄位，不能移動或隱藏。

<br>

## 付款方式

### Stripe 和 PayPal Business 有什麼不同？

🙋 [Stripe](https://stripe.com/payments) 和 [PayPal Business](https://www.paypal.com/us/business/website-payments) 都可以處理信用卡付款，也都適用 Chopin 的自動對帳功能。但是我們比較 **推薦使用 Stripe**。

使用 Stripe 時，客人可以直接在網路商店輸入信用卡資訊，相較之下，PayPal 會是一個彈出視窗，且付款手續多了幾步，可能比較容易導致顧客放棄完成訂單。

[閱讀更詳細的比較](https://wpforms.com/stripe-vs-paypal-which-one-is-better/)

### PayPal.Me 和 PayPal Business 有什麼不同？

🙋 雖然 PayPal 個人或商業帳號都可以設定 [PayPal.Me 連結](https://www.paypal.com/paypalme/)，但這只是一個快速連結，依然屬於手動付款。代表客人仍要點選連結、登入，才能付款。

[PayPal Business](https://www.paypal.com/us/business/website-payments) 則可以直接引導顧客付款，並確保他們完成交易。 

### 如何設定 PayPal.Me？

1. 註冊一個 PayPal 帳號。
2. 進入 [PayPal.Me 網站](https://www.paypal.com/paypalme/) 並點選 `Create Your PayPal.Me Link`
3. 輸入你的專屬 URL。會長得像：PayPal.Me/YourBrand
4. 也可以在 [PayPal.Me 設定](https://www.paypal.com/paypalme/my/settings)裡添加帳號顯示圖、背景圖和個人化訊息等等

<br>

## 其他問題

### 如何縮網址？

🙋可以使用縮網址服務，像是 [Bitly](https://bitly.com/)。亦可升級每月$10的 [Basic Plan](https://apiobuild.com/#pricing) ，即可擁有一個 apio 的短網址（`chopin.apiobuild.com/YOURNAME`)。如果你已經有自己的 domain，我們也可以幫你轉移。

### 如何取得 LINE 網址？

🙋 個人帳號
1. 進入 LINE 後點選 <i class="fas fa-user-plus"></i> (加入好友)。
2. 點選 `邀請` ，再選擇 `簡訊傳送邀請`。
3. 隨便選擇一個好友並按 `邀請`，此時並不會自動幫你寄送簡訊。
4. 畫面即會跳轉至你的簡訊軟體，並在編輯視窗裡出現你的專屬網址，長得會像是：line.me/ti/p/XXXX

🙋 群組
1. 在群組訊息中點擊上方 <i class="fas fa-bars"></i> 標示並選擇 `邀請`。
2. 點選 `邀請網址` 後即會出現 `複製邀請網址`的選項。長得會像是：line.me/R/ti/g/XXXX

### 如何開啟自動寄送訂單確認信功能？

🙋先在 [Post-it](https://telescope.apiobuild.com/app/post-it/configure) 授權我們使用你的 gmail:
1. 先點選 `View Emails` 再按加號 (+)
2. 登入你的google帳號
3. 點選 `允許` (`Allow`) 授予 apio 以您的名義傳送電子郵件
4. 再回到 [Chopin](https://telescope.apiobuild.com/app/chopin) 的訂單設定 (Order Settings）打勾 `Send  Order Confirmation` 

[更多 Post-it 或訂單確認信的資訊\...](https://apiobuild.com/blog/introducing-post-it-email-automation-service/)


<style>
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 80%;
}
</style>
