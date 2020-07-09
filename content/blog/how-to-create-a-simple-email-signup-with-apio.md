---
title: "How to Create a Simple Email Sign Up with Waitress"
image: /images/blog/mailbox.png
date: 2020-06-26
tags: ["waitress", "telescope", "tutorial", "email", "marketing", "google", "sheets", "website", "google-sheet"]
---

Are you struggling with finding a FREE service to collect emails? Are you overwhelmed by all those fancy features provided by email marketing solutions? In this post, we will show you how to collect email from your website visitors with google sheet. [Waitress](https://telescope.apiobuild.com/app/waitress) - apio's google sheet API microservice will help you to build relationship with users in **less than 10 minutes** and **without using email marketing platforms**.

[Read more: Why you don’t need email marketing tools (yet) to collect emails?](https://apiobuild.com/blog/collect-email-addresses-without-email-marketing-tools/)

## Step 1: Create Email List Google Sheet

Create a google sheet that you'll be using as your **mailing list**. Copy and paste the following columns to the sheet:

<div class="table-box table-warning table-responsive px-2 py-2">
<table class="center">
  <tbody>
    <tr>
      <td class="wide">name</td>
      <td class="wide">email</td>
      <td class="wide">created</td>
    </tr>
  </tbody>
</table>
</div>

<br><br>

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/mail-list-google-sheet.mp4" type="video/mp4" />
</video>

## Step 2: Authorize Catalog Google Sheet on Telescope

Go to **[Telescope(apio microservices platform)](https://telescope.apiobuild.com/)**. Log in into your **existing google account**. 

Then go to **[Waitress](https://telescope.apiobuild.com/app/waitress)** and follow the instruction in the **configure tab** to authorize your google sheet. This way, only you can access your sheet through our API.

- Share editor permission with [Waitress](https://telescope.apiobuild.com/app/waitress/configure).
- Copy and past the google sheet URL, hit Authorize
- Copy the returned route URL 

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/authorize-email-google-sheet.mp4" type="video/mp4" />
</video>

## Step 3: Add New Token

Go to your account in Telescope and click **View Token**, you will be asked to sign in again for security.

Then add a new token:

- Alias: nickname for the token
- Target Audience: the domain you’ll be calling the API from. If you’re testing locally, you could use `http://localhost:8080` for example.

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/add-token.mp4" type="video/mp4" />
</video>

## Step 4: Configure Token

Expand the token you just created, paste the **route URL from [Step 2](#step-2-authorize-catalog-google-sheet-on-telescope)** under Access Policy. In the Request Method dropdown, select **POST**.

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/token-post.mp4" type="video/mp4" />
</video>

If you forget to copy the returned route URL from [Step 2](#step-2-authorize-catalog-google-sheet-on-telescope): 
1. Simply go back and recreate it. You might need to delete the meta tab in google sheet in order to configure again.

2. Put the following in route field `waitress/gsheets/<your google sheet id>`. You can find your Google Sheet id in the url, which is the number after `spreadsheet/d/` and before `/edit`.

<img src="/images/blog/delete-meta.png" class="post-img">

## Step 5: Add Sign-up Form to Website

Copy and paste the html form to your website:

#### Sign-up form

```html
<div class="container py-3">
 <div class="card">
   <div class="card-body">
     <form>
       <div class="row">
         <div class="form-group col-4">
           <input type="text" class="form-control" id="fname" placeholder="Enter name"> 
         </div>
         <div class="form-group col-6">
           <input type="text" class="form-control" id="femail" placeholder="Enter email"> 
         </div>
         <div class="col">
           <button type="button" class="btn btn-primary" onclick="submitForm()">Sign Up</button>
         </div>
       </div>
     </form>
   </div>
 </div>
</div>
```

This will create the form like this:

<img src="/images/blog/signupform.png" class="post-img">

#### Token

- Insert the **token** you retrieve from Telescope account after `let token = Bearer`.
- Insert the **Google Sheet id** after `/gsheets/`

<img src="/images/blog/copytoken.png" class="post-img">

```html
<script type="text/javascript">
 let token = "Bearer <your telescope token>"
 let url =
"https://trampoline.apiobuild.com/router/waitress/gsheets/<your google sheet id>";
 
 function submitForm() {
   var http = new XMLHttpRequest();
   http.open("POST", url, true);
   http.setRequestHeader("Authorization", token);
   http.setRequestHeader("Content-type", "application/json");
 
   let name = document.getElementById('fname').value;
   let email = document.getElementById('femail').value;
   let created = new Date().toISOString();
   let payload = [
   {
     Name: name,
     Email: email,
     Created: created
   },
   ];
   http.send(JSON.stringify(payload));
 }
</script>
```

Ta da! There you have a simple sign-up form to collect emails from your website visitors! Give it a try yourself. 🎉

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
    max-width: 70%;
}
</style>
