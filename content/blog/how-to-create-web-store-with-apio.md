---
title: "How to Create Web Store with Chopin and Waitress"
image: /images/blog/chopinwebsite.png
date: 2020-07-08
tags: ["chopin", "waitress", "telescope", "tutorial", "ecommerce", "google-sheet", "google", "website", "documentation"]
---

[Chopin by apio](https://telescope.apiobuild.com/app/chopin) is a static online store generator that allows you to configure your online store in just a few clicks. In this post, we'll show you how you create an online store with google sheet using [Waitress](https://telescope.apiobuild.com/app/waitress) (apio's google sheet API microservice). Try now and start selling your products online!

<!--more-->

🛍️ [Visit Demo Store](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C117090713962028193035/7a8c0376-0fd0-4093-894f-e6d0200444d4)

🛍️ [Read more: How does Chopin compare to website builders and ecommerce services](https://apiobuild.com/blog/create-an-online-store-for-free/)

🛍️ [中文版教學](https://apiobuild.com/blog/how-to-create-web-store-with-apio-ch/)

## TL; DR

The set-up process is easy to follow. Click [here](https://telescope.apiobuild.com/flow/chopin-stores) to start creating your Chopin store. Then check this article to see what to include in your catalog google sheet and [configure your store](https://apiobuild.com/blog/how-to-configure-chopin-store/) .

Troubleshooting? Check these [frequently asked questions](https://apiobuild.com/blog/troubleshoot-chopin-store/).

Prefer to learn from videos? Watch this [three-minute tutorial video](https://youtu.be/BWYpITLKzXI) to get started!

## Step 1: Create a Store

Go to [Telescope (apio microservices platform)](https://telescope.apiobuild.com/). Log in with your existing google account by selecting `Sign in with Google` in the pop-up window.

Then go to [Chopin Stores](https://telescope.apiobuild.com/flow/chopin-stores) to start creating your store. First step is naming your store. Store name cannot be changed later.

<video width="100%" controls style="align: center">
<source src="/video/name-store.mp4" type="video/mp4" />
</video>

## Step 2: Add Catalog Google Sheet

You will need two google sheets (one served as **product catalog**, another one for **collecting order**). Follow the direction to create a new google sheet as your catalog, where you input product details and prices.

1. Create Sheet: Click <i class="fas fa-plus"></i> (plus sign) to create a google sheet, that will be used as catalog.
2. Populate Data: Click <i class="fas fa-copy"></i> (copy sign) to copy the example data, then paste it to your sheet.
3. Share: Click the email address to copy it. Go to your google sheet, the click `Share` at the top right corner. Add the copied email address as Editor.
4. Authorize: Copy this google sheet URL and paste it in the Google Sheet URL field. Then click <i class="fas fa-unlock"></i> (unlock sign) to authorize. After authorization, only you can access your sheet through our API.

*You can replace example data with your own later. See this [article](https://apiobuild.com/blog/how-to-configure-chopin-store/) for more information.*

<video width="100%" controls style="align: center">
<source src="/video/create-catalog-sheet.mp4" type="video/mp4" />
</video>

## Step 3: Add Order Google Sheet

Repeat the same process to create another google sheet, which will be storing **new orders** that customers submit to your store. 

1. Create Sheet: Click <i class="fas fa-plus"></i> (plus sign) to create another google sheet, that will be used to collect order.
2. Populate Data: Click <i class="fas fa-copy"></i> (copy sign) to copy the header columns, then paste it to your sheet.
3. Share: Click the email address to copy it. Go to your google sheet, the click `Share` at the top right corner. Add the copied email address as Editor. 
4. Authorize: Copy this google sheet URL and paste it in the Google Sheet URL field. Then click <i class="fas fa-unlock"></i> (unlock sign) to authorize.

You can manage this order sheet in your preferred way by adjusting the order of columns or adding more columns (i.e. order_shipped, order_completed, note, etc).

<video width="100%" controls style="align: center">
<source src="/video/create-order-sheet.mp4" type="video/mp4" />
</video>

## 🎉 Congratulations! You've just created a store!

Check out your store now (it should look like [this](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C106308532747537725517/3b99cc9c-6c28-45dd-9786-8521fe0a2e47)) and be proud of yourself! 

You can proceed to [Step 4](#step-4-add-email-confirmation) to finish setting up email confirmation, or go to [Chopin](https://telescope.apiobuild.com/app/chopin) to configure your store.

<video width="100%" controls style="align: center">
<source src="/video/view-configure-store.mp4" type="video/mp4" />
</video>


## Step 4: Add Email Confirmation

You can enable email confirmation with any Gmail account. Click <i class="fas fa-plus"></i> (plus sign) to grant us permission to send email on your behalf.

*This step is optional. You don't have to if you don't plan to send email confirmation. You can also add this later by going to the [Post-it app](https://telescope.apiobuild.com/app/post-it).*

<video width="100%" controls style="align: center">
<source src="/video/authorize-email.mp4" type="video/mp4"/>
</video>

## Summary

Now you are a proud owner of a Chopin store! Finish setting up your store by following this [article](https://apiobuild.com/blog/how-to-configure-chopin-store/) to update your catalog google sheet and configure your store.

Happy “chopin”! 🛍️