---
title: "Introducing Post-It: Communication Automation Service"
image: /images/blog/email-post-it.png
date: 2020-08-16
tags: ["email-automation", "email", "chopin", "online-shop", "post-it", "tutorial", "use-case","order-confirmation"]
---

Announcing our new service: **[Post-it](https://telescope.apiobuild.com/app/post-it)** - a communication automation service. We wrap various communication APIs in one place. You can send pre-templated messages from your own email address and other social accounts over API (we currently support **Gmail**) with simple configuration. In this post, we will show you how you can use Post-it with Chopin (apio\'s online store creator) to send automated order confirmation. 

## Use Case: Automated Order Confirmation

Order confirmation is a great way to **signal customers that the store has received their orders** and **remind customers if there's any pending actions** (for example: payment confirmation, delivery schedule, etc.). We offer [templated confirmation](#email-template), so you don't have to design one. We also add [action buttons](#action-button) to allow customers to respond messages easily. 

The confirmation email can act as a conversation starter between merchants and customers. **You can keep all the customer communication in one place (your inbox) and manage order progress in email thread.**

For example, if you provide manual payment methods (Zelle, Venmo), some customers might tell you they've paid through facebook messenger, some might use emails, some might not tell you. It's overwhelming to track customer communications when they're all over the place (email, text, Facebook, Instagram, etc.). With Post-it's email service, customers can reply that confirmation email simply by clicking the payment confirmation button. This email thread can be used to coodinate delivery instruction, shipping status, out-of-stock notifications and more. 

🛍️ [Don\'t have an online store? Follow this step-by-step guide to create one with Chopin for free!](https://apiobuild.com/blog/how-to-create-web-store-with-apio)

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/action-button-demo.mp4" type="video/mp4" />
</video>

### Email Template

Let's take a closer look at our templated order confirmation email:

**Sender:** It will show the email is sent from `your store name` with the gmail address provided. You will be able to find a copy in your gmail sent box. The customers can also directly reply the email to you rather than to a non-human email.

**Subject Line:** It will show "Your Order from `your store name` + `order confirmation number`"

<img src="/images/blog/email-subject.png" class="post-img">

**Body:** It will include following order information:
    
- Customer's Name

- Order Summary

- Order Number and Order Placement Time

- Payment Reminder (if applicable)

- Store Logo and Social Plug-Ins (if applicable)

- Disclaimer: We don't want our customers to misunderstand these emails as spam, so we explained why they receive this message.

<img src="/images/blog/order-email-template.png" class="post-img">


### Action Button

Currently we offer **two automated responses** for customers to notify store owners when:

1. they have paid through one of the manual payment options

2. they would like to cancel order

<img src="/images/blog/action-button.png" class="post-img">

In the first scenario (Payment Confirmation), the owners can verify the payment status after receiving the customers' emails. Then they can use this email thread to further confirm the order has been processed properly and other detail coordinations.

In the latter scenario (Cancel Order), the owners will get instant notification about a cancelation. They can also use this email to follow up why the customers want to cancel order. These feedbacks are valuable for store owners to provide better products and services.

*Note: More templates and action button customization coming soon. Feel free to [drop us a message](https://apiobuild.com/forms/business/) if you have any genius idea to share!*

### Tutorial

Below we will show you how to automate the process of sending order notifications to your customers. In this example, we combine Post-it with [Chopin (apio\'s online store creator)](https://telescope.apiobuild.com/app/chopin/configure) to communicate with shoppers. 

#### Step 1: Grant Gmail Access to Post-it

Go to [Post-it](https://telescope.apiobuild.com/app/post-it/configure) on Telescope, apio's app platform. Follow the instruction to grant apio access to send email on your behalf.

1. Click `View Emails` and then the plus sign (+) to add an email
2. Log in to your google account in the pop-up window
3. Click `Allow` to grant apio access to send email on your behalf


#### Step 2: Turn on Email Confirmation Feature on Chopin

Then, go to [Chopin](https://telescope.apiobuild.com/app/chopin/configure) to turn on the email confirmation feature. 

In the **Order Settings** section, check `Send Order Confirmation` box.

Now try place an order with your online store or [ our demo store](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C117090713962028193035/7a8c0376-0fd0-4093-894f-e6d0200444d4), you will receive an email confirmation with order details and options to follow up with the owner!

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/turn-on-post-it.mp4" type="video/mp4" />
</video>

## Summary

Today we demonstrated how to set up automated order confirmation and how you can use these email threads to manage your customer communications. We will discuss more ways to utilize email automation at another time. [Try Post-it now](https://telescope.apiobuild.com/app/post-it/configure) and keep your customers "Post-it"!

Happy posting! 📝

<style>
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 100%;
}
</style>