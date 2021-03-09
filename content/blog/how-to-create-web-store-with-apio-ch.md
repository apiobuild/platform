---
title: "如何使用Chopin輕鬆建立網路商店"
image: /images/blog/chopinwebsite.png
date: 2020-08-04
tags: ["chopin", " waitress ", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation", "教學", "網路開店"]
---

[Chopin by apio](https://telescope.apiobuild.com/app/chopin) 是一個簡單的靜態網路商店生成器，讓你不用會寫程式，只要幾鍵設定即可創建一家網路商店。且只要連結 Google Sheet，即可輕鬆上架商品跟管理訂單。這篇文章我們會教你如何使用 Google Sheet 搭配 [Waitress (apio\'s google sheet API)](https://telescope.apiobuild.com/app/waitress) 建立自己的網站。跟著我們的教學，開一間自己的網路商店吧！

<!--more-->

🛍️ [示範商店馬上逛](https://chopin.apiobuild.com/demo-store)

🛍️ [延伸閱讀：Chopin 與其他電商平台比較](https://apiobuild.com/blog/create-an-online-store-for-free/)

🛍️ [English Tutorial](https://apiobuild.com/blog/how-to-create-web-store-with-apio/)

## TL; DR

我們簡化了商店設立流程，點擊[這裡](https://telescope.apiobuild.com/flow/chopin-stores)開始建立你的 Chopin 商店!

商店建立完成後，可以參考[這篇文章](https://apiobuild.com/blog/how-to-configure-chopin-store-zh/)，內文有詳細說明各項設定。遇到技術問題時，可以參考這篇[「常見問題」](https://apiobuild.com/blog/troubleshoot-chopin-store-zh/)。

## Step 1: 建立新商店

以你的 Google 帳號登入 [Telescope 平台 (apio microservices platform)](https://telescope.apiobuild.com/)，請選擇 `Sign in with Google`。

然後選取 [Chopin Stores](https://telescope.apiobuild.com/flow/chopin-stores) 建立新商店，遵照網站指示完成第一步：命名商店。

⚠️ 注意：此商店名稱之後無法更改

<video width="100%" controls style="align: center">
<source src="/video/name-store.mp4" type="video/mp4" />
</video>

## Step 2: 新增商品目錄 Google Sheet

過程中你會需要準備兩個 google sheet（商品目錄及訂單），現在先按照網站指示建立一個用來當作**商品目錄**的 google sheet。

1. 建立新表單 (Create Sheet): 點擊 <i class="fas fa-plus"></i> (加號)建立用作商品目錄的 google sheet。
2. 填入資料 (Populate Data): 點擊 <i class="fas fa-copy"></i> (複製符號) 複製範例資料，並貼上於剛剛新建立的 google sheet 上。
3. 分享權限 (Share): 點擊 Waitress 的帳號以複製，回到剛剛建立的 google sheet 點選右上角的 `共用` (`Share`)，加入 Waitress 的帳號，並將其權限設為可以編輯（editor)。可取消點選通知分享人。
4. 授權 (Authorize): 複製此 google sheet 連結，並貼上於"Google Sheet URL" 欄位，點擊 <i class="fas fa-unlock"></i> （解鎖符號) 以授權。這個步驟確保只有你可以用我們的 API 讀取這些 google sheet 上的資料。

*之後會有機會可以讓你把範例資料換成自己的商品資料，請參考此篇[教學](https://apiobuild.com/blog/how-to-configure-chopin-store-zh/)*

<video width="100%" controls style="align: center">
<source src="/video/create-catalog-sheet.mp4" type="video/mp4" />
</video>

## Step 3: 新增訂單 Google Sheet

以類似的步驟創建另一個google sheet 作為**收集訂單**之用，每筆顧客下訂的資料都會自動登錄在這個 google sheet 裡。

1. 建立新表單 (Create Sheet): 點擊 <i class="fas fa-plus"></i> (加號)建立用作收集訂單的 google sheet。
2. 填入資料 (Populate Data): 點擊 <i class="fas fa-copy"></i> (複製符號) 複製標題列，並貼上於剛剛新建立的 google sheet 上。
3. 分享權限 (Share): 點擊 Waitress 的帳號以複製，回到剛剛建立的訂單 google sheet 點選右上角的 `共用` (`Share`)，加入 Waitress 的帳號，並將其權限設為可以編輯（editor)。可取消點選通知分享人。
4. 授權 (Authorize): 複製此 google sheet 連結，並貼上於"Google Sheet URL" 欄位，點擊 <i class="fas fa-unlock"></i> （解鎖符號) 以授權。

可以自由調整標題列中各欄位的順序，也可以自己添增欄位，都不會影響訂單資料寫入。

<video width="100%" controls style="align: center">
<source src="/video/create-order-sheet.mp4" type="video/mp4" />
</video>

## 🎉 恭喜! 您成功創建了一個網路商店!

點擊 `Go To Store` 預覽你的商店，如果你使用我們提供的範例商品資料，你的店應該會長的像[這樣](https://chopin.apiobuild.com/google-oauth2%7C106308532747537725517/3b99cc9c-6c28-45dd-9786-8521fe0a2e47)。

接下來你可以繼續[步驟 4](#step-4-新增-email-確認信功能) 加上 email 確認信功能，或是到 [Chopin app](https://telescope.apiobuild.com/app/chopin)  設定網路商店細節。

## Step 4: 新增 Email 確認信功能

點擊 <i class="fas fa-plus"></i>(加號) 把你希望用來寄送訂單確認信的 Gmail 帳號加入，請在彈出視窗選擇同意給予 apio 以你的名義寄送電子郵件。

*如果不打算寄送確認信，或是想要稍後再添加此功能，可以之後再從 [Post-it app](https://telescope.apiobuild.com/app/post-it) 添加。*

<video width="100%" controls style="align: center">
<source src="/video/authorize-email.mp4" type="video/mp4"/>
</video>

## 總結

四步驟輕鬆建立網路商店，現在你可以參考這篇文章了解如何[更新商品目錄 Google Sheet](https://apiobuild.com/blog/how-to-configure-chopin-store/) 以添加自己的商品資訊，及如何從 [Chopin app](https://telescope.apiobuild.com/app/chopin) 設定外觀、聯絡資訊、折扣等等細節。

祝您開張大吉！🛍️

<style>
.center {
  margin-left:auto;
  margin-right:auto;
}
.wide {
  width: 5%;
}
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 100%;
}
</style>
