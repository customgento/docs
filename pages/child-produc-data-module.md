---
title: Child Product Data module
permalink: child_product_data_module.html
summary: "The Child Product Data Viewer Module is a powerful extension for Magento, designed to enhance the user experience and provide customers with detailed information about products. With this module installed, customers gain the unique opportunity to easily access and explore the data of child products associated with products."
sidebar: home_sidebar
toc: false
---

## Description

The **Child Product Data** is a feature-rich extension for Magento, designed to elevate the user experience and provide customers with detailed information about products. With this module installed, customers gain the unique opportunity to easily access and explore the data of child products associated with products.

### Key Features:

1. **Seamless Hyva Compatibility:** The Enhanced Child Product Data Viewer Module is fully compatible with the Hyva theme, ensuring a smooth integration and an aesthetically pleasing presentation. Your online store can now leverage the power of Hyva's modern design and user-friendly interface while providing enhanced product information.
x`
2. **Universal Theme Support:** This module has been carefully crafted to be compatible with a wide range of themes. Whether you're using the default Magento theme or any other custom theme, the Child Product Data Viewer will flawlessly adapt, offering consistent functionality across your store.

3. **Customizable System Configuration:** We understand that each store has unique requirements. That's why we have introduced useful fields in the Magento system configuration. Store administrators can now customize the display and behavior of the Child Product Data Viewer Module to perfectly align with their specific needs.

4. **Intuitive User Interface:** Customers will enjoy an intuitive and user-friendly interface that makes browsing through child product information a breeze. The data is presented in an organized and visually appealing manner, helping customers make well-informed decisions.

5. **Developer-Friendly Architecture:** For developers, the Child Product Data Module offers an easily integratable solution with well-documented code. It allows for smooth implementation, ensuring that your store's performance remains top-notch.

## Usage Instructions
If you are using Hyva theme you do not have to config the plugin and you can go to the next step, but you are using other themes or custom theme you need to first config 
the module, In this path `Store => Config => Catalog => Catalog => Child Product Data`.
You can see there are multiple fields here and you need to add your related selectors in the textarea fields, each line refers to a specific DOM.

![Settings configuration]({{ "images/child-product-data/child-product-data-settings-fields.png" }} "Settings configuration")

After that it is completely is ready for use, just create a configurable product and then add some child with different data. You would see the after for example clicking on colors the title will be changed.

![Output]({{ "images/child-product-data/child-product-data-output.png" }} "Output")

## Requirements
- PHP >= 5.5.0
- Mage_Catalog
- Mage_Checkout
- Mage_Core
- Mage_Sales
