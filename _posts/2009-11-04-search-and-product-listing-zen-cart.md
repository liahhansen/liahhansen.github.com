---
layout: post
title: Search and Product Listing in Zen Cart
---
{{ page.title }}
================

I've been working out some bugs in the search functionality that arose from some customization of the product listing.  The files I've been editing are scattered across many different folders and I thought it would be helpful to list all the files and what is in them.

The heart of the product listing for both searches and category displays is held in a variable called $listing_sql. There are two files where $listing_sql is built:

* includes/index_filters/default_filter.php

* includes/modules/pages/advanced_search_result/header_php.php

These files contain conditional statements that determine what SQL query should be executed.

Both files send $listing_sql to:

* includes/modules/product_listing.php

This file processes the SQL output into strings of html.
