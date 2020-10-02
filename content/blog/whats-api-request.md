---
title: "What's API Request and How to Estimate my Costs?"
image: /images/blog/money.png
date: 2020-09-30
tags: ["documentation", "pricing", "engineering"]
---

apio as a software platform, we provide various APIs for business automation and toolings. You can think of API as outsourcing a simple task from you or your customer to our platform. Anything you don't want to do: either manually or pay someone to do it, you make a call to apio platform and we'll do it automatically for you. In this post, you can find simple explanation of API request and estimate your monthly cost per our [pricing plan](https://apiobuild.com/#pricing).

## An API Request Example

Take [Post-It](https://apiobuild.com/blog/introducing-post-it-email-automation-service/), our email automation service, for example. We integrate it with [Chopin](https://apiobuild.com/blog/create-an-online-store-for-free/#introducing-chopin) to send order confirmation. This task, if not using our API, you could setup google sheet update notification email, anytime you receive a notification, you can manually copy items ordered and customer email from google sheet and send the order confirmation to your customers accordingly.

The task is obviously tedious and that's where our API comes in. We understand your pain so we offer a simple integration to watch for the update, based on the order submitted, send a confirmation to the customer for you. This task that we automated for you, counts as "1" API request.

## Chopin API Request Flow

Throughout the lifecycle of a Chopin store visit, there are various API involved:

<img src="/images/blog/chopin-order-api-request-flow.jpg" style="width: 100%"></img>

When a user clicks on your store URL, our platform will:

1. Make sure the **request is legit** and not abusing our API
2. If it's a Chopin store request, it will make a request on your behalf to **access product data** on your google sheet
3. If the customer submits an order, it will make a request on your behalf to **update order data** on your google sheet
4. If you enable email confirmation, it will make another request on your behalf to **send email** to the customer

*Note: the dashed-double-direction arrow indicates an authentication request + a service request. The safety and security of all services running on our platform is our utmost concern, therefore, any service request will be authenticated on your behalf.*

🛍️ [Read more: quick introduction to online store creator Chopin](https://apiobuild.com/blog/create-an-online-store-for-free/)

## Long Story Short

Although we want to be transparent about how our pricing and platform work, we understand you have better things to do other than learning how our platform API works.

Here's a quick summary:

- When you **make an impression** (no purchase), there's a total of **4 requests**
  - 2 requests to chopin: auth + chopin service
  - 2 requests to waitress: auth + product catalog from google sheet

- When **a purchase is made**, there's a total of **8 requests**
  - 2 requests to chopin: auth + chopin service
  - 2 requests to waitress: auth + get product catalog from google sheet
  - 2 requests to waitress: auth + update order google sheet
  - 2 requests to post-it (if enabled): auth + send email on your behalf to customer

**The more services integration you added to your chopin store, the more API requests it'd make and the more it'd cost.**

## Monthly Cost Calculator

{{< rawhtml >}}
<div class="card" style="padding: 20px">
  <div class="row align-items-center text-center">
    <div class="col col-12 col-md-4 py-3">
      Number of Visits
    </div>
    <div class="col col-12 col-md-8 text-left">
      <input
        class="range-slider"
        id="visits"
        type="range"
        value="1500"
        min="500"
        max="10000"
        step="500"
        style="width: 70%"
      >
      <h4 class="range-value-badge text-right">
        <span class="badge badge-primary" id="visits-val">1500</span>
      </h4>
    </div>
  </div>
  <div class="row align-items-center text-center">
    <div class="col col-12 col-md-4 py-3">
      Number of Transactions
    </div>
    <div class="col col-12 col-md-8 text-left">
      <input
        class="range-slider"
        id="transactions"
        type="range"
        value="50"
        min="10"
        max="500"
        step="10"
        style="width: 70%"
      >
      <h4 class="range-value-badge text-right">
        <span class="badge badge-primary" id="transactions-val">50</span>
      </h4>
    </div>
  </div>

  <div class="row align-items-center text-center">
    <div class="col col-12 col-md-4 py-3">
      Monthly Requests
    </div>
    <div class="col col-12 col-md-8">
      <span id="monthly-requests">6200</span>
    </div>
    <div class="col col-12 col-md-4 py-3">
      Monthly Cost
    </div>
    <div class="col col-12 col-md-8">
      <span id="monthly-cost">$6</span>
    </div>
  </div>
  
</div>

<style>
  .range-slider {
    vertical-align:middle;
  }
  .range-value-badge {
    vertical-align:middle;
    display: inline;
  }
</style>

<script>
const slide = () => {
  const sliders = $('.range-slider');

  sliders.each((_, slide) => {
    $(slide).on('change', (e) => {
      const val = $(e.target).val();
      const id = $(e.target).attr('id');
      const badge = $(`#${id}-val`);
      badge.html(val)
      calculate();
    })
  });
};

const calculate = () => {
  const visits = parseInt($("#visits-val").text());
  const trans = parseInt($("#transactions-val").text());
  const requests = (visits - trans) * 4 + trans * 8;
  const cost = Math.max(5, Math.floor(requests / 1000));
  $("#monthly-requests").html(requests);
  $("#monthly-cost").html("$" + cost);
};

slide();
</script>
{{< /rawhtml >}}

## Scenarios: Cost Estimation

Let's do a quick comparison given different scenarios so you could get an idea of actual cost:

| Scenario        | Starting Out | Growing Audience <br> (Most Common) | Recurring Customers |
| --------------- | ------------ | ----------------------------------- | ------------------- |
| Visits          | 500          | 1500                                | 2500                |
| Transactions    | 10           | 50                                  | 100                 |
| Conversion Rate | 2%           | 3.33%                               | 2.5%                |
| Total Requests  | 2040         | 6200                                | 10400               |
| Total Cost (mo) | $5           | $6                                  | $10                 |

{{< rawhtml >}}
<style>
  table{
    width: 100%;
    text-align: center;
  }
  thead>tr {
    height: 100px;
  }
  tbody>tr{
    height: 50px;
  }
</style>
{{< /rawhtml >}}

### Hobbyist

We offer [a forever free tier](https://apiobuild.com/#pricing) for you to test the water. You can have up to 5000 requests per month and have Amazon product recommendation on your Chopin store.

### Starting Out

You just started a new business and built your customer base from scratch. You probably would have 500 visitors and 10 transactions each month (2% conversion).

It'll be a total of 2040 requests consisted of:

- impressions: 4 * 490 = 1960 requests
- purchases: 8 * 10 = 80 requests

**In our [basic pricing plan](https://apiobuild.com/#pricing), monthly cost will be a total of $5**

- fixed: $5 (with 5000 requests included)

### Growing Audience (Most Common)

You've gradually grow your fan base and have a pretty stable clientele. You probably would have 1500 visitors and 50 transactions each month (3.33% conversion).

It'll be a total of 6200 requests consisted of:

- impressions: 4 * 1450 = 5800 requests
- purchases: 8 * 50 = 400 requests

**In our [basic pricing plan](https://apiobuild.com/#pricing), monthly cost will be a total of $6**

- fixed: $5 (with 5000 requests included)
- volume: $5 for 1200 requests ($1 per 1000 requests)

### Recurring Customers

You've cerated your own empire with many loyal customers and heavy traffic to your website. At this point, you would probably have 2500 visitors and 100 transactions each month (2.5% conversion).

It'll be a total of 10400 requests consisted of:

- impressions: 4 * 2400 = 9600 requests
- purchases: 8 * 100 = 800 requests

**In our [basic pricing plan](https://apiobuild.com/#pricing), monthly cost will be a total of $10**

- fixed: $5 (with 5000 requests included)
- volume: $5 for 5400 requests ($1 per 1000 requests)

*Feel free to contact our sales team via <a href="milto:apiobuild@gmail.com">email</a> or [Facebook Messenger](https://m.me/apiobuild) if you're still not sure about the cost!*


## Summary

The state of e-commerce and no-code web development platform is extremely competitive. We want to bring an alternative perspective to the competition: **more options and functionality does not solve business problems better.**

Well-designed suite of toolings specifically for small business owners could help aspiring business owners off the ground to validate their products and ideas much faster. The flexibility to quickly pivot, experiment or even taking a break could be extremely crucial in the early stage of businesses.

For those who are just starting out, you could spend your valuable time learning an e-commerce platform to build a website. We argue, however, it's so much more important to get off the ground fast, learn about your customers and improve your products and services. After all, for a business to truly succeed, it's all about the customers.

Let apio help you to choose your own set of tools and grow the business together!

Happy Building Businesses! 💼
