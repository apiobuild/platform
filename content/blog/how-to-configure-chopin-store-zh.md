---
title: "如何設定 Chopin 網路商店"
image: /images/blog/setting.png
date: 2020-08-05
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation", "教學", "網路開店"]
---

建立了 [Chopin](https://telescope.apiobuild.com/app/chopin) 商店後，接下來需要把商品目錄 google sheet 中的範例資料抽換成你想販賣的商品，並且客製商店外觀和加上其他細節設定。這篇文章會手把手教你 google sheet 每個儲存格代表的意思，以及所有我們支援的設定，讓你輕鬆完成一個適合自己的商店！

<!--more-->

🛍️ [還沒有 Chopin Store? 跟著這篇教學建立商店](https://apiobuild.com/blog/create-an-online-store-for-free-ch/)

🛍️ [參考常見問題](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/)

## 更新商品目錄

如果你跟著我們的[教學](https://apiobuild.com/blog/how-to-create-web-store-with-apio-ch)，並且使用提供的範例資料建立商店，你的商店目前應該會長的像[這樣](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C106308532747537725517/3b99cc9c-6c28-45dd-9786-8521fe0a2e47)。

我相信你應該捨不得賣出 Cool Cat 和 Funny Cat，接下來請按照以下說明更新商品目錄 Google Sheet，更新過程中內容會即時反映在網路商店。

各儲存格對應的內容：

- name: 每個產品的獨立編碼 (product id)，只能使用**英文、數字、連接號(-)或底線(＿)，不能有空格**
- nickname: 顯示在網站的產品名稱，支援任何語言文字或表情符號
- description *(非必須)*: 產品敘述
- product_url *(非必須)*: 產品外部連結
- image_url: 產品圖片網址或 YouTube 連結。每個產品可以有多個影像網址，以逗號相隔 (,) [*如何取得圖片網址](#如何取得手邊圖片的網址呢)
- price: 產品價錢，不需輸入金錢符號 ($)
- max_qty: 每個顧客可購買的上限，**如果設定 max_qty 為0, 會顯示 Coming Soon**
- category *(非必須)*: 不同的產品分類。每個產品可以有多個分類，以逗號相隔 (,)
- hide: 在這格打上 "x" (或是其他字母符號)，該產品即不會顯示在網站上
- no_tax: 在這格打上 "x" (或是其他字母符號)，該產品不會被計算稅

*注意：每列之間不得穿插空白列*

👗 [可以參考這篇文章設定有多個選項的產品](https://apiobuild.com/blog/how-to-add-options-to-products/)

範例：
<img src="/images/blog/catalog-sample.png" class="post-img">

## 客製化你的商店

可以從 [Chopin app](https://telescope.apiobuild.com/app/chopin) 進到商店的設定頁面，除了商店名稱與 Waitress APIs這兩個欄位外，其他設定都可以隨時更改，存檔後更新網路商店頁面即會看到更新內容。

點擊 <i class="fas fa-save"></i> (儲存符號) 存檔更新內容。點擊 <i class="fas fa-trash-alt"></i> (垃圾桶符號) 可刪除這間網店（刪除後無法回復）。

### 商店資訊 (Store Information)

- Store Name: 網路商店的名稱，[建立商店](https://apiobuild.com/blog/how-to-create-web-store-with-apio-ch/#step-1-建立新商店)時已提供，無法更改。
- Logo url *(非必須)*: logo 圖片網址。 [*什麼是圖片網址？](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/#如何取得手邊圖片的網址呢)
- Store Description *(非必須)*: 商店敘述，最多250字。
- Announcement *(非必須)*: 此通知會出現在頁面最上方，每次出現約5秒，可以拿來放特價訊息或其他通知。

### 外觀 (Layout)

- Store Background Image url *(非必須)*: 背景圖案連結。
- Store Background Color *(非必須)*: 可以從調色盤選取顏色或輸入 [hex code](https://htmlcolorcodes.com/)。
- Remove Description Whiteout: 移除商片敘述的半透明白色背景。
- Message to show when the product has max_qty = 0 *(非必須)*: 當商品目錄中的`max_qty` = 0，該商品在網站上會顯示 `Coming Soon!`。此欄位供你自由填入適合的字樣，例如 `Out of Stock`, `Back in October` 等等。

### 訂單設定 (Order Settings)

- Required Input in Order Form: 預設只有規定顧客一定要填寫 Email 才能成立訂單，可以在這裡選擇其他必填欄位，包括顧客名、聯絡電話和地址。
  - Customer Name
  - Customer Phone Number
  - Customer Address
- Remove Customer Address Field: 如果你販賣虛擬商品或是只提供取貨選項，可以移除訂單中的地址欄位。
- Add Optional Note Section: 可以新增一欄位供顧客填寫備註資訊。
*我們建議你請客人於此提供客製商品資訊（像是蛋糕上的糖霜字樣），而非用來與客人聯繫寄送細節*
- Set Order Minimum: 輸入顧客成立訂單的最低消費金額。
- Send Order Confirmation: 點選此功能，顧客將在下單成功後收到 email 確認信。如果你沒有在建立商店時提供[此權限](https://apiobuild.com/blog/how-to-create-web-store-with-apio-ch/#step-4-新增-email-確認信功能)，可以到 [Post-it app](https://telescope.apiobuild.com/app/post-it/) 另行設定。

📫 [了解更多關於 Post-It 與自動確認信](https://apiobuild.com/blog/introducing-post-it-email-automation-service/#tutorial)

### 聯絡方式與社群媒體 (Contact Information)

- Email: 預設是你登入使用的google email，但也可以更改。
- Facebook: facebook專頁的網址 (例：https://www.facebook.com/apiobuild)
- 電話: 請包含＋號和國碼(美國即為 +1)，不用輸入連接號(-)或括號 (例：+17181234567)
- Line: line 的個人或群組專屬網址，可參考[這篇教學](https://www.pkstep.com/archives/5261)
- Instagram: instagram 的帳號非網址，不用輸入 @ (例：apiobuild)
- Phone Number: 電話號碼前請加國碼(美加: +1)，不需加 其他符號分隔 (例： +17181234567)

點選 <i class="fas fa-plus"></i> (加號) 添加聯絡方式。如果需要編輯，只要點選同一個聯絡方式，輸入新的內容後再按加號，即會更新。也可以按 <i class="fas fa-minus"></i> (減號) 刪除資訊。

### 付款方式 (Payment Methods)

- Zelle: 填入 Zelle 帳號（電子信箱或電話號碼）
- Venmo: 填入 Venmo 帳號
- e-transfer: 填入 e-transfer 帳號
- PayPal: 如果你打算使用 [PayPal business account](https://www.paypal.com/us/business)讓顧客付款，[請聯絡我們](https://apiobuild.com/forms/business/)
- Pay at Pick-Up: 勾選此選項，可以同時出現其他付款方式與店取選項。

如果沒有新增任何付款方式，預設會是以 "Submit Order" 按鈕送出訂單。可以添加兩樣以上的付款方式。如果有其他付款方式的需求，歡迎[聯絡我們](https://apiobuild.com/forms/business/)！

*注意：Zelle, Venmo, E-Transfer 屬於手動付款，結帳會是在 Chopin 網路商店外線下發生*

### 運費 (Shipping)

- Shipping Option: 可以設立多個運費選項，點選 <i class="fas fa-plus"></i> (加號) 新增。
- Free Shiping: 可設定免運金額標準。
- Delivery Zipcode: 如果你只配送到某些區域，可在此輸入該區域 zipcode 串並以逗號 (,) 分開。顧客填寫地址時，若 zipcode 不在這些範圍時即無法成立訂單。目前只支援美國地址。

### 折扣 (Discount)

- Discount Type: 可以選擇要滿額折價 (dollar) 或是打折 (percentage)。
- Discount Category: 如果只想針對某分類產品打折，可以在此填入商品目錄中的分類 (category)。
- Discount Threshold: 設定購物須滿多少額度才享有折扣。

### 稅 (Tax)

填入你所在城市的消費稅率。如果將 Tax Rate 設為0，即不會顯示稅率。

### Waitress API

這些是建立商店時自動填入的，如果需要將商品目錄或訂單 google sheet 更新為新試算表，請<a href="mailto:apiobuild@gmail.com">聯絡我們</a>。

## 總結

新功能持續開發中，並會更新於此篇文章中。如果你有建議或是想客製部分功能，歡迎<a href="mailto:apiobuild@gmail.com">寫信</a>或是使用 [Facebook 訊息](https://m.me/apiobuild)聯絡我們。不論預算大小， apio 團隊致力於為您提供合適的客製軟體服務 🚀

<style>
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 100%;
}
</style>
