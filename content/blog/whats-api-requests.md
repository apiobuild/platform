---
title: "What's API Requests and How to Estimate my Costs?"
image: /images/blog/chopinwebsite.png
date: 2020-09-30
tags: ["documentation", "pricing", "engineering"]
---

apio as a software platform we provide various API for business automation and toolings. You can think of API as outsourcing a simple task from you or your customer to our platform. Anything you don't want to do: either manually or pay someone to do it, you make a call to apio platform and we'll do it automatically for you.

## An API Request Example

Take Post-It, our email automation service, for example - we integrate it with Chopin to send order confirmation. This task, if not using our API, you could setup google sheet update notification email, anytime you receive a notification, you can manually copy items ordered and customer email from google sheet and send the order confirmation to your customers accordingly.

The task is obviously tedious and that's where our API comes in. We understand your pain so we offer a simple integration to watch for the update, based on the order submitted, send a confirmation to the customer for you - this task that we automated for you, counts as "1" API request.

## Chopin API Request Flow

Throughout the lifecycle of a Chopin store visit, there are various API involved:

<img src="/images/blog/chopin-order-api-request-flow.jpg" style="width: 100%"></img>

When a user click on your store URL, our platform will:

1. Make sure the request is legit and not abusing our API
2. If it's a Chopin store request, it will make a request on your behalf to access product data on your google sheet
3. If the customer submits an order, it will make a request on your behalf to update order data on your google sheet
4. If you enable email confirmation, it will make another request on your behalf to send email to the customer

Note: the dashed double direction arrow indicates an authentication request + a service request. The safety and security of all services running on our platform is our utmost concern, therefore, any service request will be authenticated on your behalf.

## Long Story Short

Although we want to be transparent about how our pricing and platform works, we understand you have better things to do besides learning how our platform API works. Here's a quick summary

- When you make an impression (no purchase), there's a total of 4 requests
  - 2 requests to chopin: auth + chopin service
  - 2 requests to waitress: auth + product catalog from google sheet

- When a purchase is made, there's a total of 8 requests
  - 2 requests to chopin: auth + chopin service
  - 2 requests to waitress: auth + get product catalog from google sheet
  - 2 requests to waitress: auth + update order google sheet
  - 2 requests to post-it (if enabled): auth + send email on your behalf to customer

The more services integration you added to your chopin store, the more API requests it'd make and the more it'd cost.

## Quick Comparison

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

## Cost Estimation Given Different Scenarios

### Starting Out

500 visitors per month and 10 (2% conversion) transactions.

It'll be a total of 2040 requests consisted of:

- impressions: 4 * 490 = 1960 requests
- purchases: 8 * 10 = 80 requests

In our basic pricing plan, monthly cost will be a total of $5

- fixed: $5 (with 5000 requests included)

### Growing Audience (Most Common)

1500 visitors per month and 50 (3.33% conversion) transactions.

It'll be a total of 6200 requests consisted of:

- impressions: 4 * 1450 = 5800 requests
- purchases: 8 * 50 = 400 requests

In our basic pricing plan, monthly cost will be a total of $6

- fixed: $5 (with 5000 requests included)
- volume: $5 for 1200 requests ($1 per 1000 requests)

### Recurring Customers

2500 visitors per month and 100 (2.5% conversion) transactions.

It'll be a total of 10400 requests consisted of:

- impressions: 4 * 2400 = 9600 requests
- purchases: 8 * 100 = 800 requests

In our basic pricing plan, monthly cost will be a total of $10

- fixed: $5 (with 5000 requests included)
- volume: $5 for 5400 requests ($1 per 1000 requests)

## Summary

The state of e-commerce and no-code web development platform is extremely competitive. We want to bring an alternative perspective to the competition: more options and functionality does not solve business problems better.

Well-designed suite of toolings specifically for small business owners could get aspiring business owners off the ground much faster to validate their products and ideas. The flexibility to quickly pivot, experiment, or even taking a break, could be extremely crucial in the early state of businesses.

For those who's just starting out, you could spend your valuable time learning a e-commerce platform to build a website and how to manage your inventory - we argue, however, it's so much more important to get off the ground fast, learn about your customers and improve your products and services. After all, for a business to truly succeed, it's all about the customers.

Happy Building Businesses.
