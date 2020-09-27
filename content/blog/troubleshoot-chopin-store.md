---
title: "Something Went Wrong? Troubleshooting Your Chopin Store"
image: /images/blog/faqs.png
date: 2020-09-25
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation"]
---

We try our best to design a fool-proof onboarding process, but things happens, if you see error messages or Patrick Star crying (hopefully really rare), let us troubleshoot together! This is a growing list of commonly asked questions regarding apio\'s static online store generator [Chopin](https://telescope.apiobuild.com/app/chopin).

Contact us (aka your favorite developer) via <a href="mailto:apiobuild@gmail.com">email</a> or [Facebook Messenger](https://m.me/apiobuild) if you don't find answers here! Bug reports and feebacks are welcomed too!

<img src="/images/blog/chopin-error.png" class="post-img">

🛍️ [Doesn\'t have a Chopin store yet? Create one today!](https://apiobuild.com/blog/how-to-create-web-store-with-apio/)

🛍️ [Read more: how to configure your Chopin store?](https://apiobuild.com/blog/how-to-configure-chopin-store/)

## Checklist

We suggest you check the followings first to detect and fix the technical issues.

### Google Sheet Data

- In catalog sheet, there should be no empty lines between rows.
- In catalog sheet, `name` of each product can not be empty nor can be characters other than numbers or alphabets. No spaces either. Product names must be unique.
- In order sheet, `order_number` has always to be the first row and cannot be hidden.
- Check if your image urls are [direct links](#why-the-images-are-not-shown-properly) by pasting them to the browser.
- Please do not modify the header data copied from tutorial.

### Chopin

- Check if you use the same log-in methods for logging in Telescope and opening a Chopin store. Click the setting button (<i class="fas fa-cog"></i>) and visit your [Telescope account](https://telescope.apiobuild.com/settings). Try sign out completely and log in again by selecting `Sign in with Google` in the pop-up window.

### Browser

- Pop-up blocker might disrupt the google sheet authorization process. Disable the plug-in, and try [authorize google sheets](https://apiobuild.com/blog/how-to-create-web-store-with-apio/#step-2-add-catalog-google-sheet) again.


## Other Questions

### How can I obtain image url?

🙋 Try image hosting services, like [Imgbb](https://imgbb.com/) or [img.onl](https://img.onl/). After uploading an image to those websites, you will get an **image url** or a **direct link** that points directly to a specific image.

<img src="/images/blog/faq-image-link.png" class="post-img">

### Why the images are not shown properly?

🙋 Make sure you copy the image url - the internet address that points directly to a specific image, rather than an entire index, webpage, or website. You can put the url in address bar to test it out. If you can see the image and only the image, then that's a working url.

🙋 If you're using images off Facebook, Instagram, or other websites that are not managed by yourself. Try moving your images to a hosting service.

### How to find image url from my website and Facebook pages?

🙋 Right-click the image > Select `Copy Image Address`. However, we recommend using an image hosting service to ensure the image urls will always be valid.

### How can I get notification when someone places a new order?

🙋 You can set up google sheet notification to get real-time updates on new order submission. At the top of your Order google sheet, click `Tools` and then `Notification Rules`. Select "when" you want to receive notifications. [Read more](https://support.google.com/docs/answer/91588?co=GENIE.Platform%3DDesktop&hl=en)

### How can I shrink my store URL?

🙋 Try URL shortener services, like [Bitly](https://bitly.com/)  or [tinyurl](https://tinyurl.com/) to make your store link easier to share. Contact us if you want to reroute your Chopin to your domain, if you already have one.

### Can I add/move/hide columns in order google sheet?

🙋 Absolutely! Feel free to add a column to write in some notes or move the column so certain information can be next to each other. **As long as you keep the title row**, our api will be able to populate data to matching fields. 

Note, `order_number` has always to be the first column and cannot be hidden.

### What should I do if I don't want to see certain data?

🙋 We don't recommend deleting any real data (actual transactions, retiring products, etc), as they're valuable for future analysis. Instead, feel free to hide the rows you don't need (Select row(s) > Right Click > Click `Hide row`) or hide the products that no longer available (see [instruction](https://apiobuild.com/blog/how-to-configure-chopin-store/#update-catalog-sheet)). 

Note, `order_number` has always to be the first column and cannot be hidden.

<style>
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 80%;
}
</style>
