---
title: "How to Create Web Store with Chopin and Waitress"
image: /images/blog/chopinwebsite.png
date: 2020-07-08
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation"]
---

[Chopin by apio](https://telescope.apiobuild.com/app/chopin) is a static online store generator that allows you to configure your online store in just a few clicks. In this post, we'll show you how you create an online store with google sheet using [Waitress](https://telescope.apiobuild.com/app/waitress) (apio's google sheet API microservice). Try now and start selling your products online in just a few clicks.

🛍️ [Visit Demo Store](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C117090713962028193035/7a8c0376-0fd0-4093-894f-e6d0200444d4)

🛍️ [Read more: How does Chopin compare to website builders and ecommerce services.](https://apiobuild.com/blog/create-an-online-store-for-free/)

🛍️ [中文版教學](https://apiobuild.com/blog/how-to-create-web-store-with-apio-ch/)

## TL; DR

We simplified the set-up process for you. Click [here](https://telescope.apiobuild.com/flow/chopin-stores) to start creating your Chopin store!

## Step 1: Create Catalog Google Sheet

You will need two google sheets (one served as catalog, another one for collecting order) created before setting up your store. 

Firstly, create a google sheet that you'll be using as your **catalog**. Copy and paste the following columns to the sheet and input your product information to corresponding cells.

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

- name: unique name/id contains **only dashes (-), underscores (_), and alphanumeric are allowed** for each product. No spaces.
- nickname: item names that will appear on the store page, they can be **any language, symbol, and even emoji**
- description *(optional)*: more information about the product
- product_url *(optional)*: link to an external web page
- image_url: url of the product image or YouTube video link (obtained via Share button). Multiple image urls can be separated by commas (,). [*What\'s image url?](#how-can-i-obtain-image-url)
- price: product price, no need to enter "$" (dollar sign)
- max_qty: maximum quantity that one customer can buy. **If max_qty = 0, it will show 'Out of Stock'**.
- category *(optional)*: to allow customer to filter products. Multiple categories can be separated by commas (,).

You can also add the following columns for more advanced options:

- hide: enter "x" (or any other characters), this product will not appear on your store
- no_tax: enter "x" (or any other characters), sales tax won't apply to this product

👗 [Check out this article if you want to sell products with multiple options](https://apiobuild.com/blog/how-to-add-options-to-products/)

*Note: There should not be empty line(s) between rows.*

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/copy-paste-catalog-google-sheet.mp4" type="video/mp4" />
</video>

## Step 2: Authorize Catalog Google Sheet on Telescope

Go to [Telescope (apio microservices platform)](https://telescope.apiobuild.com/). Log in with your **existing google account** by selecting `Sign in with Google` in the pop-up window.

Then go to [Waitress](https://telescope.apiobuild.com/app/waitress) and follow the instruction on the **configure tab** to authorize your google sheet: 
1. Click `Share` at the top right corner of your google sheet
2. Add the Waitress as an editor
3. Copy and paste your google sheer URL. Hit `Authorize`

After authorization, only you can access your sheet through our API.

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/authorize-catalog-google-sheet.mp4" type="video/mp4" />
</video>

## Step 3: Create Order Google Sheet

Repeat [Step 1](#step-1-create-catalog-google-sheet) and [Step 2](#step-2-authorize-catalog-google-sheet-on-telescope) to **create another google sheet** with different header. 

Copy and paste the following columns to the sheet, no need to input additional information. This sheet will be storing **new orders** that customers submitted to your store. 

You can manage this order sheet in your preferred way by adjusting the order of columns or adding more columns (i.e. order_shipped, order_completed, note, etc)

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

*Note: Don't worry if somehow you can't copy everything, just make sure you have **'order_number' in the A1 cell**. The rest will magically appear when an order is placed.*

## Step 4: Create the Store

After configuring both catalog and order sheets in waitress app, we can now head to [Chopin](https://telescope.apiobuild.com/app/chopin) to create our store. Enter the following information to the corresponding fields. You can update this information anytime (**except store name and google sheet URLs**) and the updates will be reflected in real-time.

#### Customize Your Store

- Store Name: name of your store
- Logo url *(optional)*: it can even be a gif
- Announcement *(optional)*: it will show at the top of your store. You can update it anytime
- Store Description *(optional)*: any information you'd like to include. Up to 250 characters
- Store Background Image url  *(optional)*: add a background image
- Store Background Color  *(optional)*: you can easily select color from swatch or [hex code](https://htmlcolorcodes.com/)

#### Contacts and Social Plug-ins

- Email: it will be your google email by default, but you can change it to a different email. If you've authorized your email through [Post-it](https://telescope.apiobuild.com/app/post-it/), you can enable the automated email delivery feature by checking the  `Send Automated Order Confirmation` box

📫 [Check out this article to set up automated email confirmation with Post-it](https://apiobuild.com/blog/introducing-post-it-email-automation-service/#tutorial)

- Facebook: full url to your facebook page (eg. https://www.facebook.com/apiobuild)
- Phone Number: start with country code (US: +1) and without dash nor brackets (eg. +17181234567)
- Line: link to your line account or line group
- Instagram: instagram handle without @, not the full url (eg. apiobuild)

#### Payment Options

- PayPal: [contact us](https://apiobuild.com/forms/business/), let us help you integrate your [PayPal business account](https://www.paypal.com/us/business)
- Zelle: provide your Zelle email or mobile number
- Venmo: provide your Venmo handle

*Note: We view Zelle and Venmo as manual payment methods, which means the payment would be handled outside of the Chopin checkout.*

#### Tax and Shipping Set-up

- Tax Rate *(optional)*: if Tax Rate = 0, it will not be shown on the store page
- Shipping Options *(optional)*: you can setup multiple options and free shipping minimum

#### Google Sheet API

- Catalog Google Sheet url: copy and paste the authorized catalog sheet URL from [Step 1](#step-1-create-catalog-google-sheet) 
- Order Google Sheet url: copy and paste the authorized order sheet URL from [Step 3](#step-3-create-order-google-sheet)

*Note: In this example, we use [Waitress google sheet API](https://telescope.apiobuild.com/app/waitress) as catalog and order API. We welcome you to bring your own API, <a href="mailto:apiobuild@gmail.com">let us know</a>!*

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/create-store.mp4" type="video/mp4" />
</video>

## Step 5: Start Selling

Voila, the store is now available at: [tinyurl.com/batmans-store](https://tinyurl.com/batmans-store)!

💡You can use URL shorten services like [bitly.com](https://bitly.com/) or [tinyurl.com](https://tinyurl.com/) to make the raw url easier to share on facebook, instagram, and among you friends.

💡Any new order will be updated on the order google sheet you created in [Step 3](#step-3-create-order-google-sheet). You can also setup [google sheet notification](https://support.google.com/docs/answer/91588?co=GENIE.Platform%3DDesktop&hl=en) to get real-time updates on new order submission.

Happy “chopin”! 🛍️

## FAQs

If you see error messages or Patrick Star crying (hopefully really rare), let us troubleshoot together! <a href="mailto:apiobuild@gmail.com">Contact us (your favorite developer) if you don't find answers here</a>!

<img src="/images/blog/chopin-error.png" class="post-img">

### Chopin
  - Go to [Step 2](#step-2-authorize-catalog-google-sheet-on-telescope), check if you authorize both of your google sheets.
  - Check if you use the same log-in methods for logging in Telescope and opening a Chopin store by click the setting button (<i class="fas fa-cog"></i>) and visit your [Telescope account](https://telescope.apiobuild.com/settings). Try sign out completely and log in again by selecting `Sign in with Google` in the pop-up window.

### Google Sheet Data
  - In catalog sheet, there should be no empty lines between rows.
  - In the catalog sheet, `name` of each product can not be empty nor can be characters other than numbers or alphabets. No spaces either. Product names must be unique.

### Browser
  - Pop-up blocker might disrupt the google sheet authorization process. Disable the plug-in, and try again from [Step 2](#step-2-authorize-catalog-google-sheet-on-telescope)


### Other Questions

#### How can I obtain image url?

🙋Try image hosting services, like [Imgbb](https://imgbb.com/) or [img.onl](https://img.onl/). After uploading an image to those websites, you will get an image url or a direct link that points directly to a specific image.

#### Why the images are not shown properly?

🙋Make sure you copy the image url - the internet address that points directly to a specific image, rather than an entire index, webpage, or website. You can put the url in address bar to test it out. If you can see the image and only the image, then that's a working url.

🙋Also try moving your images to a hosting service.

#### How to find image url from my website and Facebook pages?

🙋Right-click the image > Select `Copy Image Address`. However, we recommend using an image hosting service to ensure the image urls will always be valid.

#### How can I get notification when someone places a new order?

🙋At the top of your Order google sheet, click `Tools` and then `Notification Rules`. Select "when" you want to receive notifications. [Read more](https://support.google.com/docs/answer/91588?co=GENIE.Platform%3DDesktop&hl=en)

#### How can I shrink my store URL?

🙋Try URL shortener services, like [Bitly](https://bitly.com/)  or [tinyurl](https://tinyurl.com/) to make your store link easier to share.

#### Can I add/move columns in order google sheet?

🙋Absolutely! Feel free to add a column to write in some notes or move the column so certain information can be next to each other. As long as you keep the title row, our api will be able to populate data to matching fields.

#### What should I do if I don't want to see certain data?

🙋We don't recommend deleting any real data (actual transactions, retiring products, etc), as they're valuable for future analysis. Instead, feel free to hide the rows you don't need (Select row(s) > Right Click > Click `Hide row`) or hide the products that no longer available (see [Step 1](#step-1-create-catalog-google-sheet)'s advanced option).


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
