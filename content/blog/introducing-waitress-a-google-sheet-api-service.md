---
title: "Introducing Waitress: A Google Sheet API Service for Email Sign Up and Beyond"
intro_image: https://media.giphy.com/media/3o6vXV8xLaq2Dc1Mkg/giphy.gif
date: 2020-06-17
---

Collecting emails from website visitors is one of the most crucial ways to grow your audience, whether you’re looking to convert subscribers to customers or to directly communicate to your clients. Like you, we thought this is easy, however, days into looking for a simple email sign-up service, we've found the answer is actually ... quote complicated.

<img src="/images/blog/complicated.png" class="post-img">

## Existing Email List Services Are Complicated

It often requires multiple steps to collect emails from your website:

1. Research an email marketing service that offers a free tier and register the service.
2. Design a sign-up form on that service.
3. Figure out how to embed their service into your website:
   - If using a website builder (WordPress, SquareSpace, Wix, etc.): check if the marketing tool provides a plug-in for easy integration.
   - If building on your own: spend more time to find how to embed the code.
4. If the sign-up form option is not provided by the selected email marketing tool, find a plug-in compatible with your website builder.

**Sometimes, you just need a simple tool to help you build the email list that doesn’t require multiple steps to implement and countless research for free solutions.**  

## Start Simple

<img src="/images/blog/questions.png" class="post-img">

As small business owner or influencer who's just testing the water, you might not need the full capacity of all the features those email marketing services offer. *(Yes, A/B testing is important, but do you need it when you only have 1000 contacts?)*

In order to focus on perfecting your product or service, you might not want to put too many resources and efforts into figure out how everything works or how it works on your website.

**At this beginning phase, we recognize that you simply want/need to send updates to about your new projects or special discounts.**  

## Introducing Waitress

[Waitress](https://telescope.apiobuild.com/app/waitress) is a lightweight API to use Google Sheet as data store for backend applications, sends subscribers’ data from sign-up form to Google Sheet.

<img src="/images/blog/sheet.png" class="post-img">

## It’s simple, easy, and low-cost

No need to be overwhelmed by how to make different services talk to each other, you just need to put a snippet of html code to your website. All the subscription entry will be sent to the Google Sheet automatically.

Especially you get to use the interface that everyone is already familiar with - Google Sheet - to update information. And you still have all the functionality to process your data: sort, filter, delete duplicate, find, etc..

Comparing with market solutions, Waitress is billed by *[insert pricing language]*. Collecting 5000 emails can just be under $??*[insert an estimate]*.

## You manage your own data

Remembering the time when you have to download the csv file from your email marketing provider, then struggle with matching the format to another digital tool.

With **Waitress**, the freedom to manage your own data makes it easier to integrate with any third-party software. Data is available through API. It's easily customizable and integrable with other third-party marketing solutions. You can easily connect the subscriber data to ticketing platform, Google Analytics, and more!

## Make team collaboration smoother

With the built-in features of Google Sheet, it’s straightforward to manage team members’ sharing permission and collaboration. There will be no mistakenly deleted contacts anymore. You can also access your list from everywhere, which is great for remote working environments.

## Bonus point for sending emails from sheets

To automate your workflow, you can even send emails from Google Sheets to different people!

## Step by Step

Snippet to add the signup form to your static website:

### Live Demo

<div class="card">
  <div class="card-body">
    <form>
      <div class="row">
        <div class="form-group col-4">
          <input type="text" class="form-control" id="vname" placeholder="Enter name">  
        </div>
        <div class="form-group col-4">
          <input type="text" class="form-control" id="vemail" placeholder="Enter email">  
        </div>
        <div class="col">
          <button type="button" class="btn btn-primary" onclick="submitForm()">Sign Up</button>
        </div>
      </div>
    </form>
  </div>
</div>
<script>
function submitForm() {
let name = document.getElementById("vname").value;
let email = document.getElementById("vemail").value;
var http = new XMLHttpRequest();
var url =
"https://trampoline.apiobuild.com/router/waitress/gsheets/1jAJPHwVQ9L37izcEKYLnrTjCnrV-e0P4NS342VMvv3U";
http.open("POST", url, true);
http.setRequestHeader(
"Authorization",
"Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVhMDYwN2U1LWIzNzctMTFlYS1hNzA3LTRkYjY3ZDFhOWVkMSIsImF1ZCI6Imh0dHA6Ly9sb2NhbGhvc3Q6MTMxMyIsImlhdCI6MTU5MjcyMTc0OSwiaXNzIjoiZ29vZ2xlLW9hdXRoMnwxMTcwOTA3MTM5NjIwMjgxOTMwMzUiLCJzdWIiOiJnb29nbGUtb2F1dGgyfDExNzA5MDcxMzk2MjAyODE5MzAzNSJ9.hAbHZ47bIiXkqwjGzafztHQ4S06zXlIX9z8SGD-uanI"
);
http.setRequestHeader("Content-type", "application/json");
let payload = [
{
    Name: name,
    Email: email,
},
];
http.send(JSON.stringify(payload));
}
</script>

<style>
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 40%;
}
</style>

