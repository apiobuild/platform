---
title: "How to Configure Your Chopin Store"
image: /images/blog/setting.png
date: 2020-07-09
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation"]
---

After creating your [Chopin](https://telescope.apiobuild.com/app/chopin) store, you now need to [1) update the catalog google sheet](#update-catalog-sheet) with your own product information; [2) finish setting up your store in Chopin app](#configure-your-store-in-chopin-app), including appearance, social accounts, discount rule, free shipping threshold, etc. In this article, we will breakdown all the google sheet fields as well as explain customization settings. Let us help you create a store tailored for your business needs!

<!--more-->

🛍️ [Follow this step-by-step tutorial to create your online store for free today!](https://apiobuild.com/blog/how-to-create-web-store-with-apio/)

🛍️ [Something wrong with your Chopin store? Check these frequently asked questions.](https://apiobuild.com/blog/troubleshoot-chopin-store/)

🛍️ [中文設定教學](https://apiobuild.com/blog/how-to-configure-chopin-store-zh/)

<div class="table-box table-warning table-responsive px-2 py-2">
<table class="center">
  <tbody>
    <tr>
   CONTENTS:

- [Update Catalog Sheet](#update-catalog-sheet)
- [Configure Your Store (in Chopin app)](#configure-your-store-in-chopin-app)
  - [Store Information](#store-information)
  - [Layout](#layout)
  - [Order Settings](#order-settings)
    - [Store Currency](#store-currency)
    - [Order Form](#order-form)
    - [Minimum Order](#minimum-order)
    - [Order Confirmation Email](#order-confirmation-email)
  - [Contact Information](#contact-information)
  - [Payment Methods](#payment-methods)
    - [Online Payment Processor](#online-payment-processor)
    - [Manual Options](#manual-options)
  - [Shipping](#shipping)
  - [Discount](#discount)
  - [Tax](#tax)
  - [Waitress API](#waitress-api)
- [Summary](#summary)
    </tr>
  </tbody>
</table>
</div>

## Update Catalog Sheet

Your store would be look like [this](https://chopin.apiobuild.com/google-oauth2%7C106308532747537725517/3b99cc9c-6c28-45dd-9786-8521fe0a2e47) if you follow the [tutorial](https://apiobuild.com/blog/how-to-create-web-store-with-apio) and use the example data provided. But I'm pretty sure you're not selling Cool Cat and Funny Cat. Now it's time to update the catalog google sheet with your own product information.

Fields are defined as the following:

- name: Unique name/id starts with any alphabet and contains **only dashes (-), underscores (_), and alphanumeric are allowed** for each product. No spaces.
- nickname: Item names that will appear on the store page, they can be **any language, symbol, and even emoji**.
- description *(optional)*: More information about the product. [*Styling with Markdown is supported](https://www.markdownguide.org/cheat-sheet/)
- image_url: URL of the product image(s). Multiple image urls can be separated by commas (,). [*What\'s image url?](https://apiobuild.com/blog/troubleshoot-chopin-store/#how-can-i-obtain-image-url)
- price: Product price, no need to enter "$" (dollar sign).
- max_qty *(optional)*: Maximum quantity that *one customer* can buy. If max_qty = 0, it will show 'Coming Soon'
- category *(optional)*: To allow customer to filter products. Multiple categories can be separated by commas (,).
- hide: Enter "x" (or any other characters), this product will not appear on your store.
- no_tax: Enter "x" (or any other characters), sales tax won't apply to this product.

Example:
<img src="/images/blog/catalog_sheet_ex1.png" class="post-img">

<br>

If you want to [sell products with multiple options](https://apiobuild.com/blog/how-to-add-options-to-products/), you will need to add below columns manually:

- option:name
- option:size
- option:flavor
- option:color

Example:
<img src="/images/blog/catalog_sheet_ex2.png" class="post-img">

⚠️ Important:
1. There should not be any empty line(s) between rows.
2. Only items with valid `name` and `price` will show on website.

If you experience any errors, [follow these FAQs and troubleshoot yourself](https://apiobuild.com/blog/troubleshoot-chopin-store/) or [contact customer support](https://m.me/apiobuild)!

<br>

## Configure Your Store (in Chopin app)

The next step is to customize your store in [Chopin](https://telescope.apiobuild.com/app/chopin) app, where you can change the layout of your online store or configure various functions. You can update this information anytime (except store name and waitress APIs) and the updates will be reflected in real-time.

⚠️ Editing Tips:
- Click <i class="fas fa-save"></i> (save sign) to save your updates. Click <i class="fas fa-trash-alt"></i> (trash can sign) to delete the store completely.
- Click <i class="fas fa-plus"></i> (plus sign) to add new information and click <i class="fas fa-minus"></i> (minus sign) to delete the information.
- To modify, just select the same option and enter with the updated information. Then click <i class="fas fa-plus"></i> (plus sign) to update.

<img src="/images/blog/i_chopin_app.png" class="post-img">

### Store Information

- Store Name: You named your store when [creating the store](https://apiobuild.com/blog/how-to-create-web-store-with-apio/#step-1-create-a-store). It cannot be modified.
- Logo url *(optional)*: Give your store a logo. [*What\'s image URL?](https://apiobuild.com/blog/troubleshoot-chopin-store/#how-can-i-obtain-image-url)
- Store Description *(optional)*: Let your customers know what your store is about, brand story, shipping/return policy, or any information you'd like to include. Up to 1000 characters. [*Styling with Markdown is supported](https://www.markdownguide.org/cheat-sheet/)
- Announcement *(optional)*: News to share with your customers.

<img src="/images/blog/a_store_info_21.png" class="post-img">

### Layout

- Store Background Image url *(optional)*: Add a background image.
- Store Background Color *(optional)*: You can easily select color from swatch or enter a [hex code](https://htmlcolorcodes.com/).
- *`[NEW]`* Page Header Height: You can adjust height of your background image. Default is 100% and it will take up the entire screen.

<img src="/images/blog/b_layout_1_21.png" class="post-img">

- Message to show when the product has max_qty = 0 *(optional)*: In catalog google sheet, when input "0" in the `max_qty` field the indicated product will show "Coming Soon!" on the website. You can customize this text your way. A few other alternatives can be "Out of Stock", "Back in October" etc.

<img src="/images/blog/b_layout_2.png" class="post-img">

### Order Settings

#### Store Currency

- *`[NEW]`* Store Currency: Default is USD (US Dollar). Choose your preferred [currency code](https://en.wikipedia.org/wiki/ISO_4217#Active_codes) from the dropdown menu.

#### Order Form

- Required Input in Order Form: By default, we only require customers to put in their emails. You can make other fields required, so you would not miss any important information.
  - Customer Name
  - Customer Phone Number
  - Customer Address
- Remove Customer Address Field: If you sell digital products or only offer store pick-up, you might not need to collect customer's addess.
- Add Optional Note Section: To add a field for customers to input any notes.

   *We recommend using this field to collect customization details (i.e. message to be put on the cake) rather than using as a communication channel*

<img src="/images/blog/c_order_1_21.png" class="post-img">

#### Minimum Order

- Set Order Minimum: Enter a dollar amount. Your customers' purchase has to achieve this minimum amount to be able to submit the order.

#### Order Confirmation Email

- Send Order Confirmation: Enable this feature, so customers can receive a confirmation email after placing an order successfully. If you didn't grant us access to send email on your behalf when [creating store](https://apiobuild.com/blog/how-to-create-web-store-with-apio/#step-4-add-email-confirmation), you can do so in [Post-it app](https://telescope.apiobuild.com/app/post-it/).

   📫 [What does the confirmation email look like?](https://apiobuild.com/blog/introducing-post-it-email-automation-service/#email-template)

- *`[NEW]`* Order Confirmation Email Subject: Customize the subject of order confirmation email. Use `<store_name>` and `<order_number>` to show the name of your store and the customer's order number.

   Default subject line is "Your Order from `<store_name>` [`<order_number>`]”. It will look like this:
   <img src="/images/blog/c_order_2.png" class="post-img">

   If you input "🎁 `<store_name>` has a surprise for you! Order number: `<order_number>`". The subject line will look like this:
   <img src="/images/blog/c_order_3.png" class="post-img">

### Contact Information

- Email: Default is the email address you used to sign into Telescope. But you can enter a different one if you wish to display a different email on website or send [confirmation emails](https://apiobuild.com/blog/how-to-configure-chopin-store/#order-confirmation-email) from that different email.
- Facebook: Full url to your facebook page or group (eg. https://www.facebook.com/apiobuild)
- Instagram: instagram handle without @, not the full url (eg. apiobuild)
- LINE: URL to your LINE account or LINE group. [*How to retrieve LINE URL](https://apiobuild.com/blog/troubleshoot-chopin-store/#how-to-retrieve-line-url)
- Phone Number: Start with country code (US: +1) and without dash nor brackets (eg. +17181234567).
- *`[NEW]`* Twitter: Twitter handle without @ (eg. apiobuild).
- *`[NEW]`* WhatsApp: WhatsApp number with country code and without dash, +,  nor brackets (eg. 12121234567).

<img src="/images/blog/d_contact_info.png" class="post-img">

### Payment Methods

Each payment method will appear as a **button**. If you don't add any payment options, there will be a **"Submit Order"** button. You can enable as many payment options as you'd like. They will replace the "Submit Order" button.

Visit our [Demo Store](https://chopin.apiobuild.com/demo-store) and see how they work in real world. If you don't see your preferred payment methods, [drop us a message](https://apiobuild.com/forms/business/)!

<img src="/images/blog/e_payment_button_21.png" class="post-img">

#### Online Payment Processor

We currently support [Stripe](https://stripe.com/payments) as online payment processor, which allows your customers pay with credit cards. [Contact us](https://apiobuild.com/forms/business/) when you've signed up Stripe and are ready to integrate them to your Chopin store.

There is a processing fee of **2.9% + 30¢**, that will be deducted directly from your Stripe account. apio doesn't take a cut from your profits! Click links below for more detailed pricing. [*Stripe v.s PayPal. Which one is better?](https://apiobuild.com/blog/troubleshoot-chopin-store/#difference-between-stripe-and-paypal-business)

- *`[NEW]`* [Stripe](https://stripe.com/pricing)

<span style="display: none">
- [PayPal](https://www.paypal.com/us/webapps/mpp/merchant-fees)
</span>

Integrating these digital payment platforms allows Chopin to **verify the transactions in realtime and post the result** to [order google sheet](https://apiobuild.com/blog/how-to-create-web-store-with-apio/#step-3-add-order-google-sheet), so you don't have to manually confirm each payment or check the amount totals.

#### Manual Options

We also support some popular manual payment options across North America. However, manual payment means that the transaction will be handled outside of the Chopin checkout. We won't be able to verify these payments either, though the payment method selected by customers will still be posted to your [order google sheet](https://apiobuild.com/blog/how-to-create-web-store-with-apio/#step-3-add-order-google-sheet).

- *`[NEW]`* [PayPal.Me](https://www.paypal.com/paypalme/): Provide your PayPal.Me link. It will look like: https://www.paypal.me/youraccount This is the only manual payment which we can auto-generate the order total amount for customers. Recommended over other manual options.
  [*How to set up PayPal.Me?](https://apiobuild.com/blog/troubleshoot-chopin-store/#how-to-set-up-paypal-me)
- [Zelle](https://www.zellepay.com/): Provide your Zelle email or mobile number.
- [Venmo](https://venmo.com/): Provide your Venmo handle.
- [E-transfer](https://www.interac.ca/en/consumers/products/interac-e-transfer/): Provide your E-Transfer email or mobile number.
- Pay at Pick-Up: Check this box if you wish to collect payment when customers pick up their orders.
- *`[NEW]`* Collect on Delivery: Check this box if you or courier will collect payment when the order is delivered to customers.

### Shipping

- Shipping Option: You can setup multiple options and the coresponding shipping cost. It will appear as a dropdown menu. You can also use this section to set pick-up dates/locations.
- Free Shipping: Set a free shipping amount.
- Delivery Zipcode: We can validate customers' addresses based on a list or lists of zipcodes provided, so you don't have to worry out-of-zone delivery. Use commas (,) to separate zipcodes. 
   *Note: We currently only support US addresses.*

<img src="/images/blog/f_shipping.png" class="post-img">

### Discount

- Discount Type: You can set up a dollar value discount or a percentage discount.
- Discount Category: Enter a category, if you wish apply discount only to this category.
- Discount Threshold: Enter a dollar value, if you wish to apply discount only to order over this amount.

<img src="/images/blog/g_discount.png" class="post-img">

### Tax

Enter the tax rate in your area. If you set Tax Rate as 0, tax option will not be shown on your online store.

If you have certain products that don't apply to sales tax, you can indicate that in the `no_tax` field in your [Catalog Google Sheet](#update-catalog-sheet).

### Waitress API

These are auto-generated when you created the store. If you need to update them, <a href="mailto:apiobuild@gmail.com">contact us</a>.

We use apio\'s own [Waitress google sheet API](https://telescope.apiobuild.com/app/waitress) as catalog and order APIs. We welcome you to bring your own API, <a href="mailto:apiobuild@gmail.com">let us know</a>!

## Summary

We are continue to update this article and grow our features. If you don't see the features you're looking for, or want to build something custom off our platform, contact us via <a href="mailto:apiobuild@gmail.com">email</a> or [Facebook Messenger](https://m.me/apiobuild). We're more than happy to build custom solutions that fit your needs and budget! 🚀

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
