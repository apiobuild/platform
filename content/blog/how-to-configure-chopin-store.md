---
title: "How to Configure Your Chopin Store"
image: /images/blog/chopinwebsite.png
date: 2020-09-24
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation"]
---

After creating a [Chopin](https://telescope.apiobuild.com/app/chopin) store, you now need to update the catalog google sheet with your own product information. You can also change the store appearance and update various setting (social plug-ins, discount rule, free shipping threshold, etc.) in Chopin app. In this article, we will breakdown what all those google sheet fields mean as well as explain all the customization setting. Let us help you create a store tailored for your business needs!

🛍️ [Follow this step-by-step tutorial to create your online store for free today!](https://apiobuild.com/blog/create-an-online-store-for-free/)

🛍️ [Something wrong with your Chopin store? Check these frequently asked questions.](https://apiobuild.com/blog/troubleshoot-chopin-store/)

## Update Catalog Sheet

Your store would be look like [this](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C106308532747537725517/3b99cc9c-6c28-45dd-9786-8521fe0a2e47)) if you follow the [tutorial](https://apiobuild.com/blog/create-an-online-store-for-free/)) and use the example data provided. But I'm pretty sure you're not selling Cool Cat and Funny Cat. Now it's time to update the Catalog sheet with your product information.

Fields are defined as the following:

- name: Unique name/id contains **only dashes (-), underscores (_), and alphanumeric are allowed** for each product. No spaces.
- nickname: Item names that will appear on the store page, they can be **any language, symbol, and even emoji**.
- description *(optional)*: More information about the product.
- product_url *(optional)*: Link to an external web page, like a facebook post or blog review.
- image_url: URL of the product image or YouTube video link (obtained via Share button). Multiple image urls can be separated by commas (,). [*What\'s image url?](https://apiobuild.com/blog/troubleshoot-chopin-store/#how-can-i-obtain-image-url)
- price: Product price, no need to enter "$" (dollar sign).
- max_qty: Maximum quantity that *one customer* can buy. If max_qty = 0, it will show 'Coming Soon'
- category *(optional)*: To allow customer to filter products. Multiple categories can be separated by commas (,).
- hide: Enter "x" (or any other characters), this product will not appear on your store.
- no_tax: Enter "x" (or any other characters), sales tax won't apply to this product.

👗 [Check out this article if you want to sell products with multiple options](https://apiobuild.com/blog/how-to-add-options-to-products/)

*Note: There should not be empty line(s) between rows.*

<img src="/images/blog/catalog-sample.png" class="post-img">


## Configure Your Store

Customize your store in [Chopin](https://telescope.apiobuild.com/app/chopin) app, where you can change the layout of your online store or configure various functions. You can update this information anytime (except store name and waitress APIs) and the updates will be reflected in real-time.

Click <i class="fas fa-save"></i> (save sign) to save your updates. Click <i class="fas fa-trash-alt"></i> (trash can sign) to delete the store completely.

### Store Information

- Store Name: You named your store when [creating the store](https://apiobuild.com/blog/how-to-create-web-store-with-apio/#step-1-create-a-store). It cannot be modified.
- Logo url *(optional)*: Give your store a logo [*What\'s image url?](https://apiobuild.com/blog/troubleshoot-chopin-store/#how-can-i-obtain-image-url)
- Store Description *(optional)*: Let your customers know what your store is about, brand story, shipping/return policy, or any information you'd like to include. Up to 250 characters.
- Announcement *(optional)*: News to share with your customers. It will be shown at the top of your store and disappear in 5 seconds.

### Layout

- Store Background Image url  *(optional)*: Add a background image.
- Store Background Color  *(optional)*: You can easily select color from swatch or enter a[hex code](https://htmlcolorcodes.com/).
- Remove Description Whiteout: To remove the white background of the store description box.

### Order Settings

- Required Input in Order Form: By default, we only require customers to put in their emails. You can make other fields required, so you would not miss any important information.
  - Customer Name
  - Customer Phone Number
  - Customer Address
- Remove Customer Address Field: If you sell digital products or only offer store pick-up, you might not need to collect customer's addess.
- Add Optional Note Section: To add a field for customers to input any notes. 
*We recommend using this field to collect customization details (i.e. message to be put on the cake) rather than using as a communication channel*
- Set Order Minimum: Enter a domore amount. Your customers' purchase has to achieve this minimum amount to be able to submit the order.
- Send Order Confirmation: Enable this feature, so customers can receive a confirmation email after placing an order successfully. If you didn't grant us access to send email on your behalf at [Step 4](#step-4-add-email-confirmation), you can do it in [Post-it](https://telescope.apiobuild.com/app/post-it/).

📫 [Check out this article to learn more about the automated email confirmation feature and Post-it](https://apiobuild.com/blog/introducing-post-it-email-automation-service/#tutorial)

### Contact Information

- Email: Default is the email you used to sign in Telescope, but you can enter another email address.
- Facebook: Full url to your facebook page or group (eg. https://www.facebook.com/apiobuild)
- Instagram: instagram handle without @, not the full url (eg. apiobuild)
- Line: Url to your line account or line group. [See here for instruction](https://www.pkstep.com/archives/5261)
- Phone Number: Start with country code (US: +1) and without dash nor brackets (eg. +17181234567)

Click <i class="fas fa-plus"></i> (plus sign) to add new contact information. If you'd like to modify it, just select the same contact method and enter with the updated information. Then click <i class="fas fa-plus"></i> (plus sign) to update. You can also click <i class="fas fa-minus"></i> (minus sign) to delete the information.

### Payment Methods

- Zelle: Provide your Zelle email or mobile number.
- Venmo: Provide your Venmo handle.
- PayPal: [Contact us](https://apiobuild.com/forms/business/) and let us help you integrate your [PayPal business account](https://www.paypal.com/us/business)

If you don't add any payment options, there will be a "Submit Order" button. You can enable as many payment options as you'd like. They will replace the "Submit Order" button. If you don't see your preferred payment methods, [drop us a message](https://apiobuild.com/forms/business/)! 

*Note: We view Zelle and Venmo as manual payment methods, which means the payment would be handled outside of the Chopin checkout.*

### Shipping

- Shipping Option: You can setup multiple options and the coresponding shipping cost. 
- Free Shiping: Set a free shipping amount.
- Delivery Zipcode: We can validate customers' addresses based on a list or lists of zipcodes provided, so you don't have to worry out of zone delivery. Use commas (,) to separate zipcodes. *Note: We currently only support US addresses*

### Discount

- Discount Type: You can set up a dollar value discount or a percentage discount.
- Discount Category: Enter a category, if you wish apply discount only to this category.
- Discount Threshold: Enter a dollar value, if you wish to apply discount only to order over this amount.

### Tax

Enter the tax rate in your area. If Tax Rate = 0, it will not be shown on the store page.

### Waitress API

These are auto generated when you created the store. If you need to update them, <a href="mailto:apiobuild@gmail.com">contact us</a>.

*Note: In this example, we use [Waitress google sheet API](https://telescope.apiobuild.com/app/waitress) as catalog and order API. We welcome you to bring your own API, <a href="mailto:apiobuild@gmail.com">let us know</a>!*

## Summary

We are continue to update this article and grow our features. If you don't see the features you're looking for, or want to build something custom off our platform, contact us via <a href="mailto:apiobuild@gmail.com">email</a> or [Facebook Messenger](https://m.me/apiobuild). We're more than happy to build custom solutions that fit your needs and budget! 🚀



<style>
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 100%;
}
</style>
