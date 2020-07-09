---
title: "How to Create Web Store with Chopin and Waitress"
image: /images/blog/chopinwebsite.png
date: 2020-07-08
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website"]
---

[Chopin by apio](https://telescope.apiobuild.com/app/chopin) is a simple online store creator that allows you to configure your online store in just a few clicks. In this post, we'll show you how you create an online store with google sheet (by [Waitress](https://telescope.apiobuild.com/app/waitress) - apio's google sheet API microservice). Try now and start selling your products online in just a few clicks.

[Read more: How does Chopin compare to website builders and ecommerce services.](https://apiobuild.com/blog/create-an-online-store-for-free/)

## Step 1: Create Catalog Google Sheet

Create a google sheet that you'll be using as your **catalog**. Copy and paste the following columns to the sheet:

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

- name: unique name/id for each product
- nickname: item names that will appear on customer's end
- description *(optional)*: product description
- product_url *(optional)*: link of product webpage
- image_url: link of product image
- price: product price
- max_qty: maximum quantity that one customer can buy. If max_qty = 0, it will show 'Out of Stock'.
- category *(optional)*: to allow customer to filter products

<br><br>

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/copy-paste-catalog-google-sheet.mp4" type="video/mp4" />
</video>

## Step 2: Authorize Catalog Google Sheet on Telescope

Go to **[Telescope(apio microservices platform)](https://telescope.apiobuild.com/)**. Log in into your **existing google account**. 

Then go to **[Waitress](https://telescope.apiobuild.com/app/waitress)** and follow the instruction in the **configure tab** to authorize your google sheet. After authorization, only you can access your sheet through our API.

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/authorize-catalog-google-sheet.mp4" type="video/mp4" />
</video>

## Step 3: Create Order Google Sheet

Repeat [Step 1](#step-1-create-catalog-google-sheet) and [Step 2](#step-2-authorize-catalog-google-sheet-on-telescope) to **create another google sheet** with different header. This sheet will be storing **new order** that customers submitted on your store.

Copy and paste the following columns to the sheet:

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
<br></br>

The last three columns are for you to manage your orders:
- status_open	
- status_paid	
- status_shipped

## Step 4: Create the Store

After configuring both catalog and order in google sheet, now we can head to [Chopin](https://telescope.apiobuild.com/app/chopin) to setup our store. Enter the **store name, logo url, catalog and order APIs**. 

*Note: In this example, we used [Waitress google sheet API](https://telescope.apiobuild.com/app/waitress) as our catalog and order APIs. So the API read: `https://trampoline.apiobuild.com/router/waitress/gsheets/<your catalog and order google sheet id>`. Google sheet id can be extrated from google sheet url: `https://docs.google.com/spreadsheets/d/<sheet-id>`.*

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/chopin-create-store.mp4" type="video/mp4" />
</video>

## Step 5: Start Selling

Voila, your store is now available at: [https://tinyurl.com/yarc2454](https://tinyurl.com/yarc2454). You can use services like [https://tinyurl.com/](https://tinyurl.com/) to make the raw url (`https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C117090713962028193035/56422174-c3bf-4e2e-9524-2ad542d84562`) easier to share on facebook, instagram, and you friends. 

Any new order will be updated on the order google sheet you created in [Step 3](#step-3-create-order-google-sheet). You can also setup [google sheet notification](https://support.google.com/docs/answer/91588?co=GENIE.Platform%3DDesktop&hl=en) to get real-time updates on new order submission.

Happy “chopin”! 🛍️

*Note: if you have nothing in the catalog, it may return an error:*  

<img src="/images/blog/chopin-error.png" class="post-img">


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
    max-width: 60%;
}
</style>
