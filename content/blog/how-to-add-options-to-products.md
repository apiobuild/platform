---
title: "How to Add Options to Products for a Chopin Store?"
image: /images/blog/option-tutorial.png
date: 2020-09-15
tags: ["telescope", "chopin", "tutorial", "product-variants", "e-commerce", "google-sheet"]
---

Are you selling products with multiple size and color options? We bring to you an advanced Chopin store that can showcase several product variations. We promise there won't be complex configuration. Just the [same catalog google sheet](https://apiobuild.com/blog/how-to-create-web-store-with-apio/#step-2-add-catalog-google-sheet) with some more columns, you will be able to sell clothes with different style and size, handmade craft with various patterns, cupcakes with multiple flavors, etc. In this tutorial, we will show you how to set up your catalog google sheet to add multiple options to your products. 

🛍️ [Create your online store for free today!](https://telescope.apiobuild.com/flow/chopin-stores)

🛍️ [Read more: quick introduction to Chopin\'s features](https://apiobuild.com/blog/create-an-online-store-for-free/)

## A Demo Clothing Store

Visit our [demo boutique shop](https://trampoline.apiobuild.com/router/chopin/store/page/google-oauth2%7C106308532747537725517/74c00629-b2a7-4e52-b58a-c35deefa8adf)! We have clothing with multiple colors and sizes as well as accessories with varied styles.

<video width="100%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/boutique-overview.mp4" type="video/mp4" />
</video>

## Tutorial

The catalog google sheet for multi-option products is just same as the catalog google sheet used in the basic Chopin store, but with some more columns. 

<div class="row py-2">
  <div class="table-box table-warning table-responsive px-2 py-2">
    <table class="center">
      <tbody>
        <tr>
          <td class="wide">option:size</td>
          <td class="wide">option:flavor</td>
          <td class="wide">option:color</td>
          <td class="wide">option:name</td>
        </tr>
      </tbody>
    </table>
  </div>
</div>

### Step 1: Choose Option Methods

There are three different ways to present your options and you can choose up to 2 options:

|             | `option-size`                                                | `option-flavor` | `option-color`  |
| ----------- | ------------------------------------------------------------ | --------------- | --------------- |
| Appearance  | Rectanglur Boxes                                             | Drop-Down Menu  | Color Circles   |
| Field Value | Custom Text                                                  | Custom Text     | HTML Color Name |
|             | <img src="/images/blog/option-size.png" class="post-img"> | <img src="/images/blog/option-flavor.png" class="post-img">|<img src="/images/blog/option-color.png" class="post-img">| 

{{< rawhtml >}}
<style>
  table{
    width: 100%;
    text-align: center;
  }
  thead>tr {
    height: 50px;
  }
  tbody>tr{
    height: 40px;
  }
</style>
{{< /rawhtml >}}

#### option:size

This field doesn't have to be **sizes** (S, M, L or 5.5, 6, 6.5), it can also be different **styles**. The text you put in to the cell will appear below the product image in the **squared box**.

`option:size` can be in any languages other than English, but cannot contain spaces. Dashes (-) is fine.

#### option:flavor

Same as above, this field doesn't have to be **flavors**. The text you put in to the cell will appear below the product image as **drop-down menu**.

`option:flavor` can be in anylanguages other than English, but cannot contain spaces. Dashes (-) is fine.

#### option:color

There are two ways to indicate your product color, which will apprear in **circle**.

1. Color Name: Just enter a color (i.e. red, blue, black, etc.). You can refer to [this list](https://htmlcolorcodes.com/color-names/) to find names for specific colors (i.e. lightskyblue, olive, and more).

2. Hex Code: Enter the 6-digit code with # sign. For example, #556B2F for olive.

### Step 2: Group Same Products Together

You also need one additional field to indicate which products should be grouped together.

#### option:name

Group the same kind of products together by inputing the same value in this field. For example, a sun dress comes with two colors - white and yellow. The `option:name` fields for these two rows have to be the same, which are `dress`, so the system can identify these *two products* are actually *two options of the same product*.

*Remember to follow the same rule of `name` field - unique name/id contains only dashes, underscores, and alphanumeric. No space is allowed.*

## Example: A Clothing Store

Now you understand what these new columns mean, let us show you how to set up a product with multiple options. 

For example, I'd like to sell this wool coat that comes with two *colors* (pink, blue) and three *sizes* (S, M, L) for each color. I will need to create 6 rows of products (2 * 3 = 6):

- Pink Coat in S size
- Pink Coat in M size
- Pink Coat in L size
- Blue Coat in S size
- Blue Coat in M size
- Blue Coat in L size

<img src="/images/blog/coat.png" class="post-img">


#### name

All these products should have a unique `name` a.k.a product id, so I decided to follow this naming guide: `coat-<color>-<size>`. Feel free to use sku numbers.

*Reminder: `name` has to be unique value, which means no products can share the same `name`.*

<img src="/images/blog/step-1-name.png" class="post-img">

#### nickname

I want the product title changes to the coresponding color, when customer tap different color options. So I put "Wool Coat Pink" in the `nickname` field for all sizes of pink coats, and "Wool Coat Blue" for all sizes of blue coats.

<img src="/images/blog/step-2-nickname.png" class="post-img">

#### option:size

There are three sizes available for each color, so I just input "S, M, L" for the `option:size` field of all pink coat rows. Repeat the same process for blue coats.

<img src="/images/blog/step-3-size.png" class="post-img">

#### option:color

I refer to [this color name list](https://htmlcolorcodes.com/color-names/) and think "pink" and "powderblue" represent the pink and blue coats perfectly. So I input "powderblue" in the `option:color` field for all blue coats and "pink" for all pink coats respectively.

<img src="/images/blog/step-4-color.png" class="post-img">

#### option:name

In order to indicate these six rows of product are actually one product with six options. I put "coat" in the `option:name` field for all the coats.

<img src="/images/blog/step-5-name.png" class="post-img">

#### Other Fields

Finally, continue to finish the other fields (`description`, `product_url`, `image_url`, `price`, `max_qty`, `category`). You can keep them all the same or customize for each option depending on whether each option has varied description, image, price, etc.

🛍️ [What does these fields mean?](https://apiobuild.com/blog/how-to-configure-chopin-store/#update-catalog-sheet)

Now you can showcase different style and sizing for this wool coat!

*Note: Given the product layouts for single option and multiple options look a little different, we suggest you organize all single-option products together and vice versa.*


<video width="80%" loop="true" autoplay="true" controls style="align: center">
<source src="/video/two-coat.mp4" type="video/mp4" />
</video>

## Summary

With Chopin, it's really convenient to manage your product in google sheet. You might need to add product variants in bulk or duplicate it from exiting variants. You don't need to follow complex instructions, just copy and paste the data in your desired way! Try Chopin today and you will be amazed by how smart you are!

Happy Adding More Products! 💰

## FAQs

Let us troubleshoot together! Contact us (your favorite developer) via <a href="mailto:apiobuild@gmail.com">email</a> or [Facebook Messenger](https://m.me/apiobuild) if you don't find answers here!

### Check Your Google Sheet Data

- `name`: there should not be any duplicate value. All `name` cells must be unique even when they share the same `option:name`.
- `option:size` and `option:flavor`: these cells should not contain spaces.

[Click here for more commonly asked questions](https://apiobuild.com/blog/troubleshoot-chopin-store/)


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
    max-width: 100%;
}
</style>