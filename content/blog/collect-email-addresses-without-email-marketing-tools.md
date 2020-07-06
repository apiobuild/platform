---
title: "Collect Email Addresses without Email Marketing Tools"
image: /images/blog/email.png
date: 2020-06-17
tags: ["waitress", "telescope", "announcement", "email", "marketing", "google", "sheets"]
---

Email sign-ups from website visitors is one of the most crucial ways to grow your audience, whether you’re looking to convert subscribers to customers or to directly communicate to your clients. In this post we'll show you how to setup easy email sign-up form for free on your website.

We built this service after looking into other email marketing platforms (<a href="https://mailchimp.com/" target="_blank">MailChimp</a>, <a href="https://www.constantcontact.com/" target="_blank">Constant Contacts</a>, <a href="https://www.omnisend.com/" target="_blank">OmniSend</a>, etc.), comparing their services, plans, and going through those articles titled <a href="https://themeisle.com/blog/best-free-email-marketing-services/" target="_blank">"Five Best Free Email Marketing Services"</a>.

We've found a simple email sign-up form is actually ... quite complicated - but it doesn't have to be.

## Introducing Waitress

<img src="/images/blog/sheet.png" class="post-img">

**<a href="https://telescope.apiobuild.com/app/waitress" target="_blank">Waitress by apio</a>** is a lightweight API to use Google Sheet as data store for backend applications, sends subscribers’ data from sign-up form to Google Sheet.

It's a straight-forward tool for small businesses or new blogger to start collecting leads.

### Live Demo

Feel free to play around here:

{{< rawhtml >}}
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
{{< /rawhtml >}}

Which updates the 
<a href="https://docs.google.com/spreadsheets/d/1jAJPHwVQ9L37izcEKYLnrTjCnrV-e0P4NS342VMvv3U" target="_blank">google sheet we set up here</a>:

{{< rawhtml >}}
<div class="container py-2">
    <div class="card">
      <div class="card-body">
        <div class="row py-2">
          <div class="col-10">
            <table class="table">
              <thead>
                <tr>
                  <th scope="col">Email</th>
                  <th scope="col">Name</th>
                  <th scope="col">Created</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td id="tname">Jane Doe</td>
                  <td id="temail">janedoe@apiobuild.com</td>
                  <td id="tcreated">some day in the future ...</td>
                </tr>
              </tbody>
            </table>
          </div>
          <div class="col">
            <button type="button" class="btn btn-primary" onclick="updateTable()">Update</button>
          </div>
        </div>
      </div>
  </div>
</div>

<script type="text/javascript">
  let token = "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImIwZGVhODAxLWI1N2ItMTFlYS1hM2M0LTYzZDEwYzc2ODJkNyIsImF1ZCI6Imh0dHBzOi8vYXBpb2J1aWxkLmNvbSIsImlhdCI6MTU5MzM3MzEwOCwiaXNzIjoiZ29vZ2xlLW9hdXRoMnwxMTcwOTA3MTM5NjIwMjgxOTMwMzUiLCJzdWIiOiJnb29nbGUtb2F1dGgyfDExNzA5MDcxMzk2MjAyODE5MzAzNSJ9.btULqOzCjZlfPZwAdscziLmorDoDdFbusaKU5EFi6E0"
  let url =
  "https://trampoline.apiobuild.com/router/waitress/gsheets/1jAJPHwVQ9L37izcEKYLnrTjCnrV-e0P4NS342VMvv3U";

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
  function updateTable() {
    let http = new XMLHttpRequest();
    http.onreadystatechange = function() {
      if (http.readyState === 4) {
        let resp = http.response.data;
        let data = resp[resp.length - 1]
        document.getElementById('tname').innerHTML = data["Name"];
        document.getElementById('temail').innerHTML = data["Email"];
        document.getElementById('tcreated').innerHTML = data["Created"];
      }
    }
    http.responseType = 'json';
    http.open("GET", url, true);

    http.setRequestHeader("Authorization", token);
    http.setRequestHeader("Content-type", "application/json");
    http.send();
  }
</script>
{{< /rawhtml >}}

Are you tempted to try this new tool? 
<a href="https://apiobuild.com/blog/how-to-create-a-simple-email-signup-with-apio/" target="_blank">Click here to follow the step-by-step tutorial and start collecting emails today!</a> 

## Existing Email List Services Are Complicated

It often requires multiple steps to collect emails from your website:

1. Research an email marketing tool that fits your needs and budget
2. Design a sign-up form
3. Get the embedded code and configure it with your website builder

**Sometimes, you just need a simple tool to help you build the email list that doesn’t require multiple steps to implement and countless research for free solutions.**  

<img src="/images/blog/complicated.png" class="post-img">

## Starting Simple

As small business owner or influencer who's just testing the water, you might not need the full capacity of all the features those email marketing services offer. *(Yes, A/B testing is important, but do you need it when you only have 1000 contacts?)*

In order to focus on perfecting your product or service, you might not want to put too many resources and efforts into figure out how everything works or how it works on your website.

**At this beginning phase, we recognize that you simply want/need to send updates to about your new projects or special discounts.**  

<img src="/images/blog/questions.png" class="post-img">

## Benefits

### Waitress is Simple, Easy, and Low-cost

No need to be overwhelmed by how to make different services talk to each other. **You just need to put a snippet of html code to your website. All the subscription entry will be sent to the Google Sheet automatically.**

Especially you get to use the interface that everyone is already familiar with - Google Sheet - to update information. And you still have all the functionality to process your data: sort, filter, delete duplicate, find, etc..

Comparing with market solutions' different pricing tiers, Waitress is billed by request. The first 5000 requests are free, which means **you can collect up to 5000 emails for free!**

### You Manage Your Own Data

Remembering the time when you have to download the csv file from your email marketing provider, then struggle with matching the format to another digital tool.

With **<a href="https://telescope.apiobuild.com/app/waitress" target="_blank">Waitress</a>**, you have the freedom to manage your own data makes it easier to integrate with any third-party software. **Data is available through API.** It's easily customizable and integrable with other third-party marketing solutions. You can easily connect the subscriber data to ticketing platform, Google Analytics, and more!

Visit **<a href="https://telescope.apiobuild.com/" target="_blank">Telescope</a>** to check out more apio's microservices offerings.

### Make Team Collaboration Smoother

With the built-in features of Google Sheet, it’s straightforward to manage team members’ sharing permission and collaboration.

There will be no mistakenly deleted contacts anymore. You can also access your list from everywhere, which is great for remote working environments.

## Summary

**<a href="https://telescope.apiobuild.com/app/waitress" target="_blank">Waitress</a> helps you to connect sign-up form with google sheets through API, and makes email collection easier.** When you are not in need of a powerful email marketing tool, this is a perfect solution for you to collect emails. <a href="https://apiobuild.com/blog/how-to-create-a-simple-email-signup-with-apio/" target="_blank">Click here to follow the step-by-step guide and start collecting emails today!</a> 

Happy emailing. 📧

<style>
.post-img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    max-width: 40%;
}
</style>
