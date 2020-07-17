---
title: "How to Create Web Store with Chopin and Waitress"
image: /images/blog/chopinwebsite.png
date: 2020-07-08
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation"]
---

[Chopin by apio](https://telescope.apiobuild.com/app/chopin) is a simple online store creator that allows you to configure your online store in just a few clicks. In this post, we'll show you how you create an online store with google sheet using [Waitress](https://telescope.apiobuild.com/app/waitress) (apio's google sheet API microservice). Try now and start selling your products online in just a few clicks.

🛍️View [Demo Store](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C117090713962028193035/7a8c0376-0fd0-4093-894f-e6d0200444d4)

🛍️[Read more: How does Chopin compare to website builders and ecommerce services.](https://apiobuild.com/blog/create-an-online-store-for-free/)

## Step 1: Create Catalog Google Sheet

Create a google sheet that you'll be using as your **catalog**. Copy and paste the following columns to the sheet and input your product information to corresponding cells.

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

Here's an example:

<img src="/images/blog/catalog-sample.png" class="post-img">
<br></br>

Fields are defined as the following:

- name: unique name/id contains **only dashes, underscores, and alphanumeric characters** for each product
- nickname: item names that will appear on the store page, they can be **any language and symbol, even emoji**
- description *(optional)*: more information of the product
- product_url *(optional)*: link to the product website
- image_url: url of the product image
- price: product price
- max_qty: maximum quantity that one customer can buy. **If max_qty = 0, it will show 'Out of Stock'**.
- category *(optional)*: to allow customer to filter products

*Note: There should not be empty line between rows.*

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/copy-paste-catalog-google-sheet.mp4" type="video/mp4" />
</video>

## Step 2: Authorize Catalog Google Sheet on Telescope

Go to [Telescope (apio microservices platform)](https://telescope.apiobuild.com/). Log in into your **existing google account**.

Then go to [Waitress](https://telescope.apiobuild.com/app/waitress) and follow the instruction on the **configure tab** to authorize your google sheet: 
1. Click `Share` at the top right corner of your google sheet
2. Add the Waitress as an editor
3. Copy and paste your google sheer URL. Hit `Authorize`

After authorization, only you can access your sheet through our API. Even us cannot edit your google sheets!

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/authorize-catalog-google-sheet.mp4" type="video/mp4" />
</video>

## Step 3: Create Order Google Sheet

Repeat [Step 1](#step-1-create-catalog-google-sheet) and [Step 2](#step-2-authorize-catalog-google-sheet-on-telescope) to **create another google sheet** with different header. 

This sheet will be storing **new order** that customers submitted on your store. So just copy and paste the following columns to the sheet, and you don't need to input other information:

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
          <td class="wide">product_qty</td>
          <td class="wide">product_price</td>
          <td class="wide">status_open</td>
          <td class="wide">status_paid</td>
          <td class="wide">status_shipped</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

*Note: Don't worry if somehow you can't copy everything, just make sure you have **'order_number' in the A1 cell**. The rest will magically appear when an order is placed.*

## Step 4: Create the Store

After configuring both catalog and order in waitress app, we can head to [Chopin](https://telescope.apiobuild.com/app/chopin) to create our store. Enter the following information to the corresponding fields. You can update this information anytime (except store name and google sheet URLs) and the updates will be reflected in real-time.

**Customize Your Store**

- Store Name: name of your store
- Logo url *(optional)*: it can even be a gif
- Announcement *(optional)*: it will show at the top of your store. You can update it anytime.
- Store Description *(optional)*: any information you'd like to include. Up to 250 characters.
- Store Background Image url  *(optional)*: add a background image
- Store Background Color  *(optional)*: you can easily select color from swatch or [hex code](https://htmlcolorcodes.com/)
- Contact and Social Plug-ins *(optional)*: currently we support email address, Facebook, Instagram, and Line

**Tax and Shipping Set-up**

- Tax Rate *(optional)*: if Tax Rate = 0, it will not be shown in the store created
- Shipping Options *(optional)*: you can setup multiple options and free shipping minimum

**Google Sheet API**

- Catalog Google Sheet url: copy and paste the authorized catalog sheet URL from [Step 1](#step-1-create-catalog-google-sheet) 
- Order Google Sheet url: copy and paste the authorized order sheet URL from [Step 3](#step-3-create-order-google-sheet)

*Note: In this example, we use [Waitress google sheet API](https://telescope.apiobuild.com/app/waitress) as catalog and order API. We welcome you to bring your own API, <a href="mailto:apiobuild@gmail.com">let us know</a>!*

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/create-store.mp4" type="video/mp4" />
</video>

## Step 5: Start Selling

Voila, the store is now available at: [tinyurl.com/batmans-store](https://tinyurl.com/batmans-store)!

💡You can use services like [tinyurl.com](https://tinyurl.com/) to make the raw url easier to share on facebook, instagram, and among you friends.

💡Any new order will be updated on the order google sheet you created in [Step 3](#step-3-create-order-google-sheet). You can also setup [google sheet notification](https://support.google.com/docs/answer/91588?co=GENIE.Platform%3DDesktop&hl=en) to get real-time updates on new order submission.

Happy “chopin”! 🛍️

# FAQs

If you see error messages or Patrick Star crying (hopefully really rare), let us trouble-shoot together! <a href="mailto:apiobuild@gmail.com">Contact your favorite developer if you don't find answers here</a>!

<img src="/images/blog/chopin-error.png" class="post-img">

#### Chopin
  - Go to [Step 2](#step-2-authorize-catalog-google-sheet-on-telescope), check if you authorize both of your google sheets

#### Google Sheet Data
  - In catalog sheet, there should be no empty lines between rows.
  - In catalog sheet, `name` of each product can not be empty nor can be characters other than numbers or alphabets. There should not be products shared the same `name`.

#### Browser
  - Pop-up blocker might disrupt the google sheet authorization process. Disable the plug-in, and try again from [Step 2](#step-2-authorize-catalog-google-sheet-on-telescope)


#### Other Questions

##### How to find image url from my website and Facebook page?

🙋Right-click the image > Select 'Copy Image Address'

##### How can I get image url for something I didn't post online?

🙋Try image hosting services, like [Imgbb](https://imgbb.com/).

##### How can I get notification when someone places a new order?

🙋At the top of your Order google sheet, click Tools and then Notification rules. Select "when" you want to receive notifications. [Read more](https://support.google.com/docs/answer/91588?co=GENIE.Platform%3DDesktop&hl=en)

##### How can I shrink my store URL?

🙋Try URL shortener services, like [tinyurl](https://tinyurl.com/) or[Bitly](https://bitly.com/) to make your store link easier to share.

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
