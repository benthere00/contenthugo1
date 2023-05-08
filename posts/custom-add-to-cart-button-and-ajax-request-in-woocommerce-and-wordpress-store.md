---
weight: 1
title: "Custom Add to Cart Button and Ajax Request in WooCommerce and WordPress Store"
date: 2023-05-08T04:53:13+08:00
lastmod: 2023-05-08T04:53:13+08:00
draft: false
author: "wpdev"
authorLink: "https://www.datacareph.com/"
description: "Creating a Custom Add to Cart Button using Ajax Request for a Seamless Checkout Experience in WooCommerce and WordPress"
images: []
featuredimage: "posts/img/woocommerce-add-to-cart.png"
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["WooCommerce","WordPress","CSS"]
categories: ["Web Development"]

lightgallery: false

toc:
  enable: true
twemoji: false
math:
  enable: false
---

## Creating a Custom Add to Cart Button using Ajax Request for a Seamless Checkout Experience in WooCommerce and WordPress

### Simple HTML and JS Approach
Here's the solution below:  

### HTML Code
```html
<button id="hi-add-button" class="hi-add-button" data-button-add="true">ADD TO CART</button>
```

### JQuery Code
```js
jQuery(document).ready(function($) {
  // Ajax Starts

  // Manually replace using your actual product ID
  const hi_products_group = [
    { product_id: 242, quantity: 2 }, // Product 1
    { product_id: 265, quantity: 1 }, // Product 2
    // You can add more here..
  ];

  let index = 0;

  function addProductToCart() {
    const getData = $('#hi-data-store').val();
    const product = hi_products_group[index];

    if (index >= hi_products_group.length) {
      // Redirect to cart or update cart widget
      window.location.href = wc_add_to_cart_params.cart_url;
      return;
    }

    // increment
    index++;

    // Send the AJAX request to add the product to the cart.
    $.ajax({
      type: 'POST',
      dataType: 'json',
      url: wc_add_to_cart_params.ajax_url,
      data: {
        action: 'woocommerce_add_to_cart',
        product_id: product.product_id,
        quantity: product.quantity,
      },
      beforeSend: function(xhr) {
        // Show loading spinner or disable button
        xhr.setRequestHeader('X-Requested-With', 'XMLHttpRequest');
        $('#hi-add-button').text('PROCEED TO CART..');
      },
      success: function(response) {
        if (index < hi_products_group.length) {
          // pause for 600ms
          setTimeout(addProductToCart, 600);
          // Add the next product to the cart
          addProductToCart();
        } else {
          // all products have been added, change button text
          $('#hi-add-button').text('ADD TO CART');
        }
      },
      error: function(xhr, status, error) {
        // Handle error
        console.log(error);
      },
    });
  }

  // '#hi-add-button' with the selector for the cart button.
  $('#hi-add-button').click(function(e) {
    e.preventDefault();
    addProductToCart();
  });
});

```

The above code has the following features 
- This even works by adding multiple products
- Make sure to replace the product IDs and quantities in the `hi_products_group` array with your actual products.
- Check that the `index` variable is initialized to `0`.
- Confirm that the `addProductToCart()` function sends the correct AJAX request to add the product to the cart.
- Verify that the `beforeSend` property of the AJAX request updates the button text appropriately.
- Check that the `success` property of the AJAX request adds the next product to the cart and updates the button text.
- Confirm that the `error` property of the AJAX request handles errors appropriately.
- Make sure that the `click` event listener for the `#hi-add-button` element calls the `addProductToCart()` function when clicked.

If the issue you were facing has been resolved by the above solution, you may stop reading at this point.

## How do I enable Ajax add to cart button in WooCommerce and Wordpress?

### Scenario 1.
If you're looking to improve your user experience and streamline your checkout process, enabling Ajax add to cart button in #WooCommerce and # is a great place to start. Ajax allows customers to add products to their cart without having to refresh the page, making the shopping experience faster and more seamless. Here's how you can enable it:

1.  Go to your WordPress dashboard and navigate to WooCommerce > Settings > Products > General.
2.  Check the box that says "Enable AJAX add to cart buttons on archives."
3.  Save changes.

With this simple change, your customers will be able to add products to their cart with just a click, without having to wait for the page to load.

## How do I add a custom add to cart button in WooCommerce?

### Scenario 2.

If you want to stand out from the crowd and create a custom add to cart button for your WooCommerce store, you can do so easily with a bit of code. Here's how:

1.  In your theme's functions.php file, add the following code:
```php
// Change "Add to cart" button text on product archives
add_filter( 'woocommerce_product_add_to_cart_text', 'custom_add_to_cart_text' );
function custom_add_to_cart_text() {
    return __( 'Buy Now', 'woocommerce' );
}

// Change "Add to cart" button text on single product pages
add_filter( 'woocommerce_product_single_add_to_cart_text', 'custom_add_to_cart_text' );
```

2.  Replace "Buy Now" with your desired text in the code above.
3.  Save changes.

Now, your custom add to cart button text will appear on both product archives and single product pages.

## How do I customize my WooCommerce cart button?
### Scenario 3.

If you want to customize the appearance of your WooCommerce cart button, you can do so with #CSS. Here's an example of how to change the background color and text color of the cart button:
```css
/* Change cart button background color */
.added_to_cart.wc-forward {
    background-color: #ff0000;
}

/* Change cart button text color */
.added_to_cart.wc-forward {
    color: #ffffff;
}
```

Simply add this CSS to your theme's stylesheet and adjust the colors to your liking. You can also target other properties of the cart button using CSS.

## Why is Ajax add to cart not working in WooCommerce?

### Scenario 4.

If Ajax add to cart is not working in WooCommerce, it could be due to a number of reasons. Here are a few things you can check:

1.  Make sure Ajax add to cart is enabled in WooCommerce settings (as described in the first section of this article).
2.  Check for conflicts with other plugins or your theme. Try disabling other plugins and switching to a default WordPress theme to see if the issue persists.
3.  Check your server logs for any errors that may be related to the issue.
4.  Make sure your WordPress installation and WooCommerce plugin are up to date.

If none of these solutions work, you may need to seek help from a developer support or simply contact us.

