---
title: "How to Create a Simple Email Sign Up with Waitress"
image: /images/blog/mailbox.png
date: 2020-06-26
tags: ["waitress", "telescope", "tutorial", "email", "marketing", "google", "sheets", "website"]
---

Are you struggling with finding a FREE service to collect emails? Are you overwhelmed by all those fancy features provided by email marketing solutions? In this post, we will show you how to set up subscription sign-up form for your website in **less than 10 minutes** and **without using email marketing platforms**. 

It only takes five steps to set up email sign up form with **[Waitress](https://telescope.apiobuild.com/app/waitress)**, the lightweight API enables you to use Google Sheet as a data store and send subscribers’ data from the sign-up form to Google Sheet.

[Read more: Why you don’t need email marketing tools (yet) to collect emails?](https://apiobuild.com/blog/collect-email-addresses-without-email-marketing-tools/)

## Step 1

Go to **[Telescope](https://telescope.apiobuild.com/)</a>**, our app platform of microservices.

Log in through your **existing google account**.

<img src="/images/blog/login.png" class="post-img">

## Step 2

Create a Google Sheet or use an existing Google Sheet file.  
Share editor permission with **Waitress (`waitress-dev@apio-277201.iam.gserviceaccount.com`)**.

<img src="/images/blog/permission.png" class="post-img">

## Step 3

Go to your account in Telescope and click **View Token**, you will be asked to sign in again for security.  
Add a new token:

- **Alias**: nickname for the token
- **Target Audience**: the domain you’ll be calling the API from. If you’re testing locally, you could use `http://localhost:8080` for example.

<img src="/images/blog/addtoken.png" class="post-img">

## Step 4

Under **Access Policy**, put the following in the **Route** field: `waitress/gsheets/<your google sheet id>`.  
You can find **your Google Sheet id** in the url, which is the number after `spreadsheet/d/` and before `/edit`.

<img src="/images/blog/gsheetid.png" class="post-img"><br>

In the **Request Method** dropdown, select **POST**.

<img src="/images/blog/accesspolicy.png" class="post-img">

## Step 5

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

Ta da! There you have a simple sign-up form to collect emails of your website visitors! Give it a try yourself. 🎉

<style>
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 70%;
}
</style>

