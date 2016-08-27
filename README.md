# BC Widget - Recent Orders
Display recent orders by customer with out being logged in using their email address that is passed as a URL parameter that can come from email marketing campaigns.

## Instructions

### Step 1. Upload widget folder to your site 
/_System/Widgets/recent-orders


----------

### Step 2. Add BC Widget - Personalization

This widget is required to be installed in order to look up customer's entity id to retrieve past order information. 

----------

### Step 4. Initialize Widget


#### Settings (if assigned variable settings are removed widget will set default option)

Option | Type | Default | Description
------ | ---- | ------- | -----------
w_recent_order_results | number | 4| Number of unique recent orders to output
w_recent_order_template  | string | /_System/Widgets/recent-orders/template/recent-order-list.tpl | Path to recent order product list layout template
w_recent_order_fallback  | string | /_System/Widgets/recent-orders/template/fallback-product-list.tpl | Path to fallback product list layout if visitor's email address is not detected or if the visitor does not have any recent orders
w_recent_order_container_class | string | row small-up-2 medium-up-3 large-up-4 | class of recent order parent element. Default layout is using foundation grid block but can customize update parent class and recent order list elements (w_recent_order_template)
w_recent_order_header | html | <h1>Recent Orders</h1> | Add any html markup inside this liquid capture element that will display the title and any other information before the recent order output.


#### Place initialization code on every template/page of your site that a visitor will enter from and in which you will need to call the visitor data.

```
{% comment -%}<!-- Settings -->{% endcomment -%}
{% assign w_recent_order_results = 4 -%}
{% assign w_recent_order_template = "/_System/Widgets/recent-orders/template/recent-order-list.tpl" -%}
{% assign w_recent_order_fallback = "/_System/Widgets/recent-orders/template/fallback-product-list.tpl" -%}
{% assign w_recent_order_container_class = "row small-up-2 medium-up-3 large-up-4" -%}
{% capture w_recent_order_header -%}
<h1>Recent Orders</h1>
{% endcapture -%}
{% assign w_recent_order_json = false -%}  
{% comment -%}<!-- Init Path -->{% endcomment -%}
{% include "/_System/Widgets/recent-orders/init.liquid" -%} 
```
### Step 6. URL Parameter

Append the below parameter to any link taking the visitor to your website

```
?w_visitor_email=username@domain.com
```

#### Example:

```
<p>Dear {tag_recipientname},</p>

<p>Check out some of your recent orders by visiting our <a href="http://www.domain.com/recent-orders?w_visitor_email=username@domain.com">website</a></p>
```
