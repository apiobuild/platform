---
title: "如何設定 Chopin 網路商店"
image: /images/blog/setting.png
date: 2020-08-05
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation", "教學", "網路開店"]
---

建立了 [Chopin](https://telescope.apiobuild.com/app/chopin) 商店後，接下來需要 [1) 抽換商品目錄 google sheet 中的範例資料成你想販賣的商品](#更新商品目錄)，並且 [2) 客製商店外觀和加上其他細節設定](#客製化你的商店)。這篇文章會手把手教你 google sheet 每個儲存格代表的意思，以及所有我們支援的設定，讓你輕鬆完成一個適合自己的商店！

<!--more-->

🛍️ [還沒有 Chopin Store? 跟著這篇教學建立商店](https://apiobuild.com/blog/create-an-online-store-for-free-ch/)

🛍️ [參考常見問題](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/)

<div class="table-box table-warning table-responsive px-2 py-2">
<table class="center">
  <tbody>
    <tr>
   內容：

- [更新商品目錄](#更新商品目錄)
- [客製化你的商店](#客製化你的商店)
  - [商店資訊 (Store Information)](#商店資訊-store-information)
  - [外觀 (Layout)](#外觀-layout)
  - [訂單設定 (Order Settings)](#訂單設定-order-settings)
    - [網站貨幣](#網站貨幣)
    - [訂購人資料](#訂購人資料)
    - [最低消費](#最低消費)
    - [訂單確認信](#訂單確認信)
  - [聯絡方式與社群媒體 (Contact Information)](#聯絡方式與社群媒體-contact-information)
  - [付款方式 (Payment Methods)](#付款方式-payment-methods)
    - [線上支付](#線上支付)
    - [手動付款](#手動付款)
  - [運費 (Shipping)](#運費-shipping)
  - [折扣 (Discount)](#折扣-discount)
  - [稅 (Tax)](#稅-tax)
  - [Waitress API](#waitress-api)
- [總結](#總結)
    </tr>
  </tbody>
</table>
</div>

## 更新商品目錄

如果你跟著我們的[教學](https://apiobuild.com/blog/how-to-create-web-store-with-apio-ch)，並且使用提供的範例資料建立商店，你的商店目前應該會長的像[這樣](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C106308532747537725517/3b99cc9c-6c28-45dd-9786-8521fe0a2e47)。

我相信你應該捨不得賣出 Cool Cat 和 Funny Cat，接下來請按照以下說明更新商品目錄 Google Sheet，更新過程中內容會即時反映在網路商店。

各儲存格對應的內容：

- name: 每個產品的獨立編碼 (product id)，英文開頭並只能使用**英文、數字、連接號(-)或底線(＿)，不能有空格**。
- nickname: 顯示在網站的產品名稱，支援任何語言文字或表情符號。
- description *(非必須)*: 產品敘述。
- product_url *(非必須)*: 產品外部連結。
- image_url: 產品圖片網址或 YouTube 連結。每個產品可以有多個影像網址，以逗號相隔 (,)。 [*如何取得圖片網址](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/#%E5%A6%82%E4%BD%95%E5%8F%96%E5%BE%97%E6%89%8B%E9%82%8A%E5%9C%96%E7%89%87%E7%9A%84%E7%B6%B2%E5%9D%80%E5%91%A2)
- price: 產品價錢，不需輸入金錢符號 ($)。
- max_qty: 每個顧客可購買的上限，**如果設定 max_qty 為0, 會顯示 Coming Soon**。
- category *(非必須)*: 不同的產品分類。每個產品可以有多個分類，以逗號相隔 (,)。
- hide: 在這格打上 "x" (或是其他字母符號)，該產品即不會顯示在網站上。
- no_tax: 在這格打上 "x" (或是其他字母符號)，該產品不會被計算稅。

範例：
<img src="/images/blog/catalog_sheet_eg1.png" class="post-img">

如果想要[將產品加上多個尺寸顏色選項](https://apiobuild.com/blog/how-to-add-options-to-products/)，你會需要手動新增以下四個欄位：

- option:name
- option:size
- option:flavor
- option:color

範例：
<img src="/images/blog/catalog_sheet_eg2.png" class="post-img">

⚠️ 注意:
1. 每列之間不得穿插空白列。
2. 若有產品沒有出現，代表 `name` 或 `price` 欄位有錯。

如果有問題或是錯誤訊息，可以參考[常見問題](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/)自行除錯，或是[聯絡客服](https://m.me/apiobuild)。

<br>

## 客製化你的商店

接下來是從 [Chopin app](https://telescope.apiobuild.com/app/chopin) 進到商店的設定頁面，除了商店名稱與 Waitress APIs 這兩個欄位外，其他設定都可以隨時更改，存檔後更新網路商店頁面即會看到更新內容。

⚠️ 編輯小幫手：
1. 點擊 <i class="fas fa-save"></i> (儲存符號) 存檔更新內容。點擊 <i class="fas fa-trash-alt"></i> (垃圾桶符號) 可刪除這間網店（刪除後無法回復）。
2. 點選 <i class="fas fa-plus"></i> (加號) 添加新資訊。也可以按 <i class="fas fa-minus"></i> (減號) 刪除資訊。
3. 如果需要編輯，只要點選同一個選項，輸入新的內容後再按加號，即會更新。

<img src="/images/blog/i_chopin_app.png" class="post-img">

### 商店資訊 (Store Information)

- Store Name: 網路商店的名稱，[建立商店](https://apiobuild.com/blog/how-to-create-web-store-with-apio-ch/#step-1-建立新商店)時已提供，無法更改。
- Logo url *(非必須)*: logo 圖片網址。 [*什麼是圖片網址？](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/#如何取得手邊圖片的網址呢)
- Store Description *(非必須)*: 商店敘述，最多250字。
- Announcement *(非必須)*: 此通知會出現在頁面最上方，每次出現約5秒，可以拿來放特價訊息或其他通知。

<img src="/images/blog/a_store_info.png" class="post-img">

### 外觀 (Layout)

- Store Background Image url *(非必須)*: 背景圖案連結。
- Store Background Color *(非必須)*: 可以從調色盤選取顏色或輸入 [hex code](https://htmlcolorcodes.com/)。
- *`[NEW]`* Page Header Height: 調整點進網站背景圖所佔螢幕的比例。*注意：若空間不夠， `Store Description` 內容將會超出首圖區。*
- Remove Description Whiteout: 移除商片敘述的半透明白色背景。

<img src="/images/blog/b_layout_1.png" class="post-img">

- Message to show when the product has max_qty = 0 *(非必須)*: 當商品目錄中的 `max_qty` 欄位為0時，該商品在網站上會自動顯示 "Coming Soon!" 但你也可以在此欄位填入其他適合的字樣，例如 "Out of Stock" 或是 "Back in October" 等等。

<img src="/images/blog/b_layout_2.png" class="post-img">

### 訂單設定 (Order Settings)

#### 網站貨幣

- *`[NEW]`* Store Currency: 預設為 USD (美元)，亦可從下拉式選單選取欲套用的[貨幣代碼](https://en.wikipedia.org/wiki/ISO_4217#Active_codes)。

#### 訂購人資料

- Required Input in Order Form: 預設只有規定顧客一定要填寫 Email 才能成立訂單，可以選擇其他必填欄位，包括顧客名、聯絡電話和地址。
  - Customer Name
  - Customer Phone Number
  - Customer Address
- Remove Customer Address Field: 如果你販賣虛擬商品或是只提供取貨選項，可以移除訂單中的地址欄位。
- Add Optional Note Section: 可以新增一欄位供顧客填寫備註資訊。 *我們建議你請客人於此提供客製商品資訊（像是蛋糕上的糖霜字樣），而非用來與客人聯繫寄送細節*

<img src="/images/blog/c_order_1.png" class="post-img">

#### 最低消費

- Set Order Minimum: 輸入顧客成立訂單的最低消費金額。

#### 訂單確認信

- Send Order Confirmation: 點選此功能，顧客將在下單成功後收到 email 確認信。如果你沒有在建立商店時提供[此權限](https://apiobuild.com/blog/how-to-create-web-store-with-apio-ch/#step-4-新增-email-確認信功能)，可以到 [Post-it app](https://telescope.apiobuild.com/app/post-it/) 另行設定。

   📫 [訂單確認信內容有什麼？](https://apiobuild.com/blog/introducing-post-it-email-automation-service/#tutorial)

- Order Confirmation Email Subject: 自訂訂單確認信件主旨，輸入 `<store_name>` 和 `<order_number>` 顯示你的店名與訂單編號。

   預設主旨是 "Your Order from `<store_name>` [`<order_number>`]”， 顯示如下：
   <img src="/images/blog/c_order_2.png" class="post-img">

   假設將主旨替換成 "🎁 `<store_name>` has a surprise for you! Order number: `<order_number>`"，則變成：
   <img src="/images/blog/c_order_3.png" class="post-img">

### 聯絡方式與社群媒體 (Contact Information)

- Email: 預設是你登入使用的google email。但若希望網站上顯示另一個 email，或是希望訂單確認信從另一個帳號寄出，也可以在這裡更改。
  *若更改email，記得要[到 Post-It授權該帳號](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/#如何開啟自動寄送訂單確認信功能)，才可以成功寄送確認信
- Facebook: Facebook 專頁或社團的網址 (例：https://www.facebook.com/apiobuild
- 電話: 請包含＋號和國碼(美國即為 +1)，不用輸入連接號(-)或括號 (例：+17181234567)
- LINE: LINE 的個人或群組專屬網址。[*如何取得LINE網址？](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/#%E5%A6%82%E4%BD%95%E5%8F%96%E5%BE%97-line-%E7%B6%B2%E5%9D%80)
- Instagram: Instagram 的帳號 (非網址)，不用輸入 @ (例：apiobuild)
- Phone Number: 電話號碼前請加國碼 (美加: +1)，不需加其他符號分隔 (例： +17181234567)
- *`[NEW]`* Twitter: Twitter 的帳號 (非網址)，不用輸入 @ (例：apiobuild)
- *`[NEW]`* WhatsApp: WhatsApp 號碼並加上國碼， 不需加 + 或其他符號分隔 (例：12121234567)

<img src="/images/blog/d_contact_info.png" class="post-img">

### 付款方式 (Payment Methods)

每個付款方式會以按鈕的方式呈現，如果沒有新增任何付款方式，預設會是以 "Submit Order" 按鈕送出訂單。可以添加兩種以上的付款方式。

可以到[範例商店](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C117090713962028193035/7a8c0376-0fd0-4093-894f-e6d0200444d4)實際體驗不同付款方式的流程。如果有其他付款方式的需求，歡迎[聯絡我們](https://apiobuild.com/forms/business/)！

<img src="/images/blog/e_payment_button.png" class="post-img">

#### 線上支付

目前支持以 [Stripe](https://stripe.com/payments) 和 [PayPal for Business](https://www.paypal.com/us/business/website-payments) 處理信用卡付款。 於上述網站開通帳號後，[聯絡我們](https://apiobuild.com/forms/business/)即可！

這兩個平台的手續費約**2.9% + 30¢**，會直接從你的營收裡扣款，可參考以下連結了解他們的詳細收費方式：

- *`[NEW]`* [Stripe](https://stripe.com/pricing)
- [PayPal](https://www.paypal.com/us/webapps/mpp/merchant-fees)

[*Stripe 和 PayPal 該選哪個？](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/#stripe-%E5%92%8C-paypal-business-%E6%9C%89%E4%BB%80%E9%BA%BC%E4%B8%8D%E5%90%8C)

若您使用線上支付平台，Chopin 可以**自動幫您對帳**，確認客人是否付款成功並將結果顯示在訂單 google sheet 上。

#### 手動付款

我們也提供以下手動付款選項，這些交易會是在 Chopin 網路商店外線下發生。雖然此類交易無法自動對帳，但我們仍會將顧客選用的付款方式記錄在訂單 google sheet 上，以利您人工對帳。

- *`[NEW]`* [PayPal.Me](https://www.paypal.com/paypalme/): 填入 PayPal.Me 連結，範例: https://www.paypal.me/youraccount。這是唯一一個雖是手動付款卻仍能幫客人產生訂單總額的選項，建議使用。
  [*如何設定PayPal.Me](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/#如何設定-paypal-me)
- [Zelle](https://www.zellepay.com/): 填入 Zelle 帳號（電子信箱或電話號碼）。
- [Venmo](https://venmo.com/): 填入 Venmo 帳號。
- [E-transfer](https://www.interac.ca/en/consumers/products/interac-e-transfer/): 填入 e-transfer 帳號。
- Pay at Pick-Up: 勾選此選項，會出現店取付款選項。
- *`[NEW]`* Collect on Delivery: 勾選此選項，會出現貨到付款選項。

### 運費 (Shipping)

- Shipping Option: 可以設立不同的運費選項，也可以用此設定不同的取貨安排（日期、地點）。
- Free Shiping: 可設定免運金額標準。
- Delivery Zipcode: 如果你只配送到某些區域，可在此輸入該區域 zipcode 串並以逗號 (,) 分開。顧客填寫地址時，若 zipcode 不在這些範圍時即無法成立訂單。目前只支援美國地址。

<img src="/images/blog/f_shipping.png" class="post-img">

### 折扣 (Discount)

- Discount Type: 可以選擇要滿額折價 (dollar) 或是打折 (percentage)。
- Discount Category: 如果只想針對某分類產品打折，可以在此填入商品目錄中的分類 (category)。
- Discount Threshold: 設定購物須滿多少額度才享有折扣。

<img src="/images/blog/g_discount.png" class="post-img">

### 稅 (Tax)

填入你所在城市的消費稅率。如果將 Tax Rate 設為0，即不會顯示稅率。

若有商品不適用消費稅，可在[商品目錄 google sheet](#更新商品目錄) 的 `no_tax` 欄位註記，即不會被計算稅率。

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
.center {
  margin-left:auto;
  margin-right:auto;
}
.wide {
  width: 5%;
}
.table-box{
  color: black;
  border-left: 6px solid #fcd236;
}
</style>
