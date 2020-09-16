---
title: "如何使用Chopin輕鬆建立網路商店"
image: /images/blog/chopinwebsite.png
date: 2020-08-04
tags: ["chopin", " waitress ", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation", "教學", "網路開店", "常見問題"]
---

[Chopin by apio](https://telescope.apiobuild.com/app/chopin) 是一個簡單的靜態網路商店生成器，讓你不用會寫程式，只要幾鍵設定即可創建一家網路商店。且只要連結 Google Sheet，即可輕鬆上架商品跟管理訂單。這篇文章我們會教你如何使用 Google Sheet 搭配 [Waitress (apio\'s google sheet API)](https://telescope.apiobuild.com/app/waitress) 建立自己的網站。跟著我們的教學，開一間自己的網路商店吧！

<!--more-->

🛍️ [示範商店馬上逛](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C117090713962028193035/7a8c0376-0fd0-4093-894f-e6d0200444d4)

🛍️ [延伸閱讀：Chopin 與其他電商平台比較](https://apiobuild.com/blog/create-an-online-store-for-free/)

🛍️ [English Tutorial](https://apiobuild.com/blog/how-to-create-web-store-with-apio/)

## TL; DR

我們簡化了商店設立流程，點[這裡](https://telescope.apiobuild.com/flow/chopin-stores)開始設定你的 Chopin 商店!

## Step 1: 新增商品目錄 Google Sheet

開始設立商店前，你會需要準備兩個 google sheet（商品目錄及訂單）。第一步是建立一個用來當作**商品目錄**的 google sheet。複製以下標題並貼到 google sheet 的標題列，然後按照說明填入你的產品資訊。

<div class="row py-2">
  <div class="table-box table-warning table-responsive px-2 py-2">
    <table class="center">
      <tbody>
        <tr>
          <td class="wide">name</td>
          <td class="wide">nickname</td>
          <td class="wide">description</td>
          <td class="wide">product_url</td>
          <td class="wide">image_url</td>
          <td class="wide">price</td>
          <td class="wide">max_qty</td>
          <td class="wide">category</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

範例：

<img src="/images/blog/catalog-sample.png" class="post-img">
<br></br>

各儲存格對應的內容：

- name: 每個產品的獨立編碼 (product id)，只能使用**英文、數字、連接號(-)或底線(＿)，不能有空格**
- nickname: 顯示在網站的產品名稱，支援任何語言文字或表情符號
- description *(非必須)*: 產品敘述
- product_url *(非必須)*: 產品外部連結
- image_url: 產品圖片網址或 YouTube 連結。每個產品可以有多個影像網址，以逗號相隔 (,) [*如何取得圖片網址](#如何取得手邊圖片的網址呢)
- price: 產品價錢，不需輸入金錢符號 ($)
- max_qty: 每個顧客可購買的上限，**如果設定 max_qty 為0, 會顯示 Out of Stock**
- category *(非必須)*: 不同的產品分類。每個產品可以有多個分類，以逗號相隔 (,)

也可以使用這些進階選項：
- hide: 在這格打上 "x" (或是其他字母符號)，該產品即不會顯示在網站上
- no_tax: 在這格打上 "x" (或是其他字母符號)，該產品不會被計算稅

*注意：每列之間不得穿插空白列*

👗 [可以參考這篇文章設定有多個選項的產品](https://apiobuild.com/blog/how-to-add-options-to-products/)

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/copy-paste-catalog-google-sheet.mp4" type="video/mp4" />
</video>

## Step 2: 授權 Google Sheet

先以 **google 帳號** (在彈出視窗點選 `Sign in with Google`) 登入 [Telescope 平台 (apio microservices platform)](https://telescope.apiobuild.com/)。

點入 [ Waitress ](https://telescope.apiobuild.com/app/waitress) 跟著 **configure tab** 上面的步驟授權 google sheet：
1. 點選 google sheet 左上角的 `共用` (`Share`)
2. 加入  Waitress  的帳號，並將其權限設為可以編輯（editor）
3. 複製貼上 google sheet 連結，並點選 `Authorize`

這個步驟確保只有你可以用我們的 API 讀取這些 google sheet 上的資料。

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/authorize-catalog-google-sheet.mp4" type="video/mp4" />
</video>

## Step 3: 新增訂單 Google Sheet

創建另一個有不同標題列的 google sheet 作為**收集訂單**之用，複製以下標題列貼到此 google sheet，無需再鍵入其它資料。並重複[步驟1](#step-1-新增商品目錄-google-sheet) 跟[步驟2](#step-2-授權-google-sheet)。

每筆顧客下訂的資料都會自動登錄在這個 google sheet 裡。

可以自由調整標題列中各欄位的順序，也可以自己添增欄位，都不會影響訂單資料寫入。

<div class="row py-2">
  <div class="table-box table-warning table-responsive px-2 py-2">
    <table class="center">
      <tbody>
        <tr>
          <td class="wide">order_number</td>
          <td class="wide">user_name</td>
          <td class="wide">user_email</td>
          <td class="wide">user_phone</td>
          <td class="wide">user_address</td>
          <td class="wide">order_created</td>
          <td class="wide">order_subtotal</td>
          <td class="wide">order_shipping_option</td>
          <td class="wide">order_shipping</td>
          <td class="wide">order_tax_rate</td>
          <td class="wide">order_tax</td>
          <td class="wide">order_total</td>
          <td class="wide">product_name</td>
          <td class="wide">product_nickname</td>
          <td class="wide">product_qty</td>
          <td class="wide">product_price</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

*小提醒：如果無法成功複製整列，不用擔心！只要第一行第一列(A1欄)有放 order_number 即可*

## Step 4: 設立網路商店

在成功用 Waitress 設定好兩個 google sheet 後，可以到平台裡的 [Chopin](https://telescope.apiobuild.com/app/chopin) 開始設立網路商店。按照說明填入你的商店資料並按照你的風格設計，除了**商店名（store name）與 google sheet URL** 外，其他選項隨時都可以更動，所有改動都會即時呈現在網路商店。

#### 客制化你的商店

- Store Name: 網路商店的名稱
- Logo url *(非必須)*: logo 網址
- Announcement *(非必須)*: 此通知會出現在頁面最上方，可以拿來放特價訊息或其他通知
- Store Description *(非必須)*: 商店敘述，最多250字
- Store Background Image url  *(非必須)*: 背景圖案連結
- Store Background Color  *(非必須)*: 可以從調色盤選取顏色或輸入 [hex code](https://htmlcolorcodes.com/)

#### 聯絡方式與社群媒體

- Email: 預設是你登入使用的google email，但也可以更改。如果你已在 Post-it 授權，打勾 `Send Automated Order Confirmation` 即會開啟自動寄送確認信功能

📫 [教學：使用 Post-it 授權你的gmail信箱](#如何開啟自動寄送訂單確認信功能)

- Facebook: facebook專頁的網址 (例：https://www.facebook.com/apiobuild)
- 電話: 請包含＋號和國碼(美國即為 +1)，不用輸入連接號(-)或括號 (例：+17181234567)
- Line: line 的個人或群組專屬網址，可參考[這篇教學](https://www.pkstep.com/archives/5261)
- Instagram: instagram 的帳號非網址，不用輸入 @ (例：apiobuild)

#### 付款方式

- PayPal: 如果你打算使用 [PayPal business account](https://www.paypal.com/us/business)讓顧客付款，[請聯絡我們](https://apiobuild.com/forms/business/)
- Zelle: 填入 Zelle 帳號（電子信箱或電話號碼）
- Venmo: 填入 Venmo 帳號

*注意：Zelle 和 Venmo 屬於手動付款，結帳會是在 Chopin 網路商店外線下發生*

#### 設定稅率與運費

- Tax Rate *(非必須)*: 如果將 Tax Rate 設為0，即不會顯示稅率
- Shipping Options *(非必須)*: 可以設立多個運費選項，亦可設定免運標準

#### Google Sheet API

- Catalog Google Sheet url: 複製貼上已授權的[步驟1](#step-1-新增商品目錄-google-sheet)中的商品目錄 google sheet 網址 
- Order Google Sheet url: 複製貼上已授權的[步驟3](#step-3-新增訂單-google-sheet)中的訂單 google sheet 網址

*在此篇教學中，我們使用 apio 的 [Waitress  google sheet API](https://telescope.apiobuild.com/app/waitress) 來讀取商品目錄跟寫入訂單資料。如果你希望連結自己的訂單管理系統，<a href="mailto:apiobuild@gmail.com">請聯絡我們</a>!*

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/create-store.mp4" type="video/mp4" />
</video>

## Step 5: 網店開張大吉

大功告成！示範影片中的商店出現在 [tinyurl.com/batmans-store](https://tinyurl.com/batmans-store)!

💡 你可以使用縮網址服務讓商店連結可以更容易地分享，像是 [bitly.com](https://bitly.com/) 或 [tinyurl.com](https://tinyurl.com/)

💡 新訂單都會出現在你在[步驟3](#step-3-新增訂單-google-sheet)建立的google sheet中。可以開啟 [google sheet 通知功能](https://support.google.com/docs/answer/91588?co=GENIE.Platform%3DDesktop&hl=zh-Hant)，這樣每次有新訂單系統就會傳送通知！

Happy “chopin”! 🛍️

## 常見問題

如果你看到錯誤訊息或是哭哭的派大星，不要緊張，可以參考以下常見問題！<a href="mailto:apiobuild@gmail.com">如果還是無法解決的話，歡迎直接聯絡工程師</a>!

<img src="/images/blog/chopin-error.png" class="post-img">

### Chopin
  - 檢查你是否兩個 google sheet 都有授權，可重複[步驟2](#step-2-授權-google-sheet)再試一次
  - 點擊設定按鈕 (<i class="fas fa-cog"></i>) 進入 [Telescope 帳戶](https://telescope.apiobuild.com/settings). 檢查登入 Telescope 和 Chopin 開店的帳號是不是相同。可以試試完全登出後，再重新以 **google 帳號** (在彈出視窗點選 `Sign in with Google`) 登入 

### Google Sheet 資料
  - 檢查商品目錄 google sheet 資料，每列之間不得穿插空白列
  - 商品目錄 google sheet 中，每個產品的 `name` 欄不得是空白，不能重複，不能出現英文數字外的字符，不能有空格

### 瀏覽器
  - 封鎖彈出視窗的功能有時候會影響 google sheet 授權過程. 可以取消此功能再重複[步驟2](#step-2-授權-google-sheet)試試


### 其他

#### 如何開啟自動寄送訂單確認信功能？

🙋先在 [Post-it](https://telescope.apiobuild.com/app/post-it/configure) 授權我們使用你的 gmail:
1. 先點選 `View Emails` 再按加號 (+)
2. 登入你的google帳號
3. 點選 `允許` (`Allow`) 授予 apio 以您的名義傳送電子郵件
4. 再回到 [Chopin](https://telescope.apiobuild.com/app/post-it/configure) 打勾 `Send Automated Order Confirmation` 

[更多 Post-it 或訂單確認信的資訊\...](https://apiobuild.com/blog/introducing-post-it-email-automation-service/)

#### 如何取得手邊圖片的網址呢？

🙋可以使用圖片網址生成服務，像是 [Imgbb](https://zh-tw.imgbb.com/) 或 [img.onl](https://img.onl/) 。成功上傳圖片成功後，會得到一串 image url 或是 direct link

#### 為什麼圖片無法顯示？

🙋檢查是否貼上完整的圖片網址，還是只是一個外部網頁連結。可以把連結放到瀏覽器網址列試試，如果只有顯示圖片，那就是正確可使用的圖片網址

🙋把圖片換到圖片網址生成服務，再試試看

#### 如何從網站或是Facebook獲得圖片網址？

🙋右鍵點擊圖片 > 選取 `複製圖片網址` (`Copy Image Address`)。但我們建議使用上述圖片網址生成服務，可確保連結不會失效

#### 如何開啟新訂單自動通知

🙋在商品目錄的 google sheet 中，按一下頂端的`工具` > `通知規則`，選取您要接收通知的時間點，[參考教學](https://support.google.com/docs/answer/91588?co=GENIE.Platform%3DDesktop&hl=zh-Hant)

#### 如何縮網址？

🙋可以使用縮網址服務，例如 [Bitly](https://bitly.com/) 或 [tinyurl](https://tinyurl.com/)

#### 可以移動或新增訂單 google sheet 中的欄位嗎？

🙋添加欄位或是移動標題列中的欄位排序都不會影響資料的寫入喔！建議可以在網站流量小的時候操作

#### 不想看到過去的訂單或是不會再製造的產品怎麼辦？

🙋不建議刪掉任何資料，這些都是之後分析顧客喜好或是成本收益的寶貴資料。可以選擇隱藏過去訂單那幾列 (選取列 > 右鍵 > `隱藏列`) 或是隱藏某幾項產品 (參考 [步驟1](#step-1-新增商品目錄-google-sheet) 的進階選項)

<style>
.center {
  margin-left:auto;
  margin-right:auto;
}
.wide {
  width: 5%;
}
.table-box{
  color: black;
  border-left: 6px solid #ffc107;
}
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 100%;
}
</style>
