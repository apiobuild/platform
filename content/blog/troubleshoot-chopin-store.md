---
title: "Something Went Wrong? Troubleshooting Your Chopin Store"
image: /images/blog/faqs.png
date: 2020-07-10
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation"]
---

We try our best to design a fool-proof onboarding process, but things happen, if you see error messages or Patrick Star crying (hopefully really rare), let us run this [checklist](#checklist) and troubleshoot together!

We also feature some commonly asked questions regarding [images](#image), [google sheets](#google-sheets), [payment methods](#payment-method), and [many more](#and-more).

[📚 We stop maintaining this troubleshooting guide. Read full content in docs →](https://apiobuild.com/docs/docs/apps/chopin/troubleshoot/)

<!--more-->

Feel free to contact us (aka your favorite developer) via <a href="mailto:apiobuild@gmail.com">email</a> or [Facebook Messenger](https://m.me/apiobuild) if you don't find answers here! Bug reports and feebacks are welcomed too!

<img src="/images/blog/chopin-error.png" class="post-img">

🛍️ [Doesn\'t have a Chopin store yet? Create one today!](https://apiobuild.com/docs/docs/apps/chopin/create-new-store/)

🛍️ [How to configure your Chopin store?](https://apiobuild.com/docs/docs/apps/chopin/product-configuration/)

## Checklist

We suggest you check the followings first to find and fix any technical issue.

### Google Sheet Data

- In catalog sheet, there should be no empty lines between rows.
- In catalog sheet, `name` of each product can not be empty nor can be characters other than numbers or alphabets. No spaces either. Product names must be unique.
- In order sheet, `order_number` has always to be the first row and cannot be hidden.
- Check if your image urls are [direct links](#why-the-images-are-not-shown-properly) by pasting them to the browser.
- Please do not modify the header data copied from tutorial.

### Chopin

- Check if you use the same log-in methods for logging in Telescope and opening a Chopin store. Click the setting button (<i class="fas fa-cog"></i>) and visit your [Telescope account](https://telescope.apiobuild.com/settings). Try sign out completely and log in again by selecting `Sign in with Google` in the pop-up window.
- Check if follow the instructions in [Chopin Flow](https://telescope.apiobuild.com/flow/chopin-stores) to create **two** google sheets, share editor access with Waitress account, and authorize.

### Browser

- Pop-up blocker might disrupt the google sheet authorization process. Disable the plug-in, and try [authorize google sheets](https://apiobuild.com/blog/how-to-create-web-store-with-apio/#step-2-add-catalog-google-sheet) again.

<br>

## Image

### How can I obtain image url?

🙋 Try image hosting services, like [Imgbb](https://imgbb.com/). After uploading an image to those websites, you will get a **direct link** or **image url** that points directly to a specific image.

<img src="/images/blog/faq-image-link.png" class="post-img">

### Why the images are not shown properly?

🙋 Make sure you copy the image url - the internet address that points directly to a specific image, rather than an entire index, webpage, or website. You can put the url in address bar to test it out. If you can see the image and only the image, then that's a working url.

🙋 If you're using images off Facebook, Instagram, or other websites that are not managed by yourself. Try moving your images to [a image hosting service](#how-can-i-obtain-image-url).

### How to find image url from my website and Facebook pages?

🙋 Right-click the image > Select `Copy Image Address`. However, we recommend using [image hosting service](#how-can-i-obtain-image-url) over copy the image urls from Facebook, as those links might be invalid after a period of time.

### Why do the images load slowly?

🙋 You might have images that are too large for the best browsing experience. We suggest you use images that size less than 500kb. You can use services like [TinyPNG](https://tinypng.com/) to reduce the file size.

## Google Sheets

### How can I get notification when someone places a new order?

🙋 You can set up google sheet notification to get real-time updates on new order submission. At the top of your Order google sheet, click `Tools` and then `Notification Rules`. Select "when" you want to receive notifications. [Read more](https://support.google.com/docs/answer/91588?co=GENIE.Platform%3DDesktop&hl=en)

### Can I add/move/hide columns in order google sheet?

🙋 Absolutely! Feel free to add a column to write in some notes or move the column so certain information can be next to each other. **As long as you keep the title row**, our api will be able to populate data to matching fields.

Note, `order_number` has always to be the first column and cannot be hidden.

### What should I do if I don't want to see certain data?

🙋 We don't recommend deleting any real data (actual transactions, retiring products, etc), as they're valuable for future analysis. Instead, feel free to hide the rows you don't need (Select row(s) > Right Click > Click `Hide row`) or hide the products that no longer available (see [instruction](https://apiobuild.com/blog/how-to-configure-chopin-store/#update-catalog-sheet)). 

Note, `order_number` has always to be the first column and cannot be hidden.

</br>

## Payment Method

### Difference between Stripe and PayPal Business?

🙋 While [Stripe](https://stripe.com/payments) and [PayPal Business](https://www.paypal.com/us/business/website-payments) both accept credit card payments and support real-time transaction verification with Chopin, **we recommend using Stripe** over PayPal Business. 

With Stripe, customers can enter their credit card information directly on the Chopin store. But PayPal requires customers sign in or enter credit card information in a pop-up window, which can result to more abandoned carts.

[Read a more in-depth comparison.](https://wpforms.com/stripe-vs-paypal-which-one-is-better/)

### Difference between PayPal.Me and PayPal Business?

🙋 Though [PayPal.Me](https://www.paypal.com/paypalme/) works for both personal and business accounts, it's still a manual payment method that requires customers to click the link, sign in to their accounts, then pay.

On the other hand, [PayPal Business](https://www.paypal.com/us/business/website-payments) integration guides your customers to enter the payment information and close the transaction for them. If they fail to submit payment, the order won't be recorded to your order google sheet.

### How to set up PayPal.Me?

1. Register a PayPal account.
2. Go to [PayPal.Me website](https://www.paypal.com/paypalme/) and click `Create Your PayPal.Me Link`.
3. Choose your unique URL. It looks like this: PayPal.Me/YourBrand.
4. You can also customize your profile in the [PayPal.Me settings](https://www.paypal.com/paypalme/my/settings), including profile photo, cover photo, and personal message.

</br>

## And More...

### How can I shrink my store URL?

🙋 Try URL shortener services, like [Bitly](https://bitly.com/)  to make your store link easier to share. You can also upgrade to [Basic Plan](https://apiobuild.com/#pricing) to own a custom apio-branded URL (`chopin.apiobuild.com/YOURNAME`) with only $10 per month. Feel free to contact us if you want to reroute your Chopin to your domain, if you already have one.

### How to retrieve LINE URL?

🙋 Personal Account
1. Open your LINE app, click <i class="fas fa-user-plus"></i> (Add friends symbol) on `Home` tab.
2. Click `Invite` and select `Invite friend by text message`.
3. Randomly select a friend and click `Invite` (Don't worry! Line will not send text automatically).
4. You will be brought to your texting app and have a draft message with your LINE URL. It will look like this: line.me/ti/p/XXXX

🙋 Group
1. Click <i class="fas fa-bars"></i> in your LINE group chat and select `Invite`.
2. Click `Invite Link` and you will see the option to `Copy invite link`. It will look like this: line.me/R/ti/g/XXXX

<style>
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 80%;
}
</style>
