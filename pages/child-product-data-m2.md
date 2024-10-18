---
title: Child Product Data for Magento 2
permalink: child-product-data-m2.html
summary: "Child Product Data dynamically displays product data from child products, as soon as a variation is selected on a product detail page of a configurable product. This way, for example the name, SKU, description and product attributes are updated and the customer can see the data of the selected variation."
sidebar: cpd_m2_sidebar
toc: false
---

## Description

On a configurable product page, you usually only see the attribute data of the configurable product itself. This extension allows you to display the data of the child products on this page and the values are dynamically changed as soon as you choose a different child product. This way, customers can easily compare the data of the child products and make a well-informed decision.

### Key Features:

1. **Dynamic Change of Product Data:** As soon as a customer chooses an option of a configurable product, the values of the following attributes are changed quick and easy:
   - Product Name
   - SKU
   - Short Description
   - Description
   - "More Information" Block
   - Related Products (performantly via AJAX)
   - Upsell Products (performantly via AJAX)
2. **Seamless Hyv&auml; Compatibility:** The extension is fully compatible with the Hyv&auml; theme, ensuring a smooth integration and an aesthetically pleasing presentation. Your online store can now leverage the power of Hyv&auml;'s modern design and user-friendly interface while providing enhanced product information.
3. **Universal Hyv&auml; Theme Support:** The extension is not only compatible with the default Hyv&auml; theme. It works also with any Hyv&auml; child theme. You only need to enter the fitting identifiers in the system configuration, and the module will do the rest.
4. **Universal Luma Theme Support:** The extension is not only compatible with the default Luma theme. It works also with any Luma child theme. You only need to enter the fitting identifiers in the system configuration, and the module will do the rest.
5. **Developer-Friendly Architecture:** For developers, Child Product Data offers an easily integrable solution with well-documented code. It follows the Magento 2 coding standards and best practices.

## Usage Instructions
Child Product Data is by default built for a clean Hyv&auml; or Luma Theme. 
If you're using such a theme or a child theme without any adaptions to the product page, you do not need to configure anything at all. 
It will work directly out of the box.  The only exception are the related and upsell products for Hyv&auml; versions 1.3.4 and below.
In case you're using such a version, please include the changes from [this Merge Request](https://gitlab.hyva.io/hyva-themes/magento2-default-theme/-/merge_requests/979/diffs){:target="_blank"} in your custom theme.  
As soon as you have a different HTML structure on your product page, you simply need to fill in the fitting identifiers under Store > Config > Catalog > Catalog > Child Product Data.  
Please mind, that a specific attribute could be included at several spots on the page. For example the name of the product is also included in the breadcrumbs. In this case, please enter each identifier in a new line. 
To find out which identifiers you need to use, you can simply inspect the HTML of your product page and look for the fitting elements.

![Settings configuration]({{ "images/child-product-data/child-product-data-settings-fields.png" }} "Settings configuration")

After entering the correct identifiers, please save the configuration and clear the cache. From now on, as soon as you choose a child product, the module will show the child data for the identifiers you configured, for example the adapted product name or the SKU.
If you do not want to change the data for a specific attribute, you can simply leave the field empty.

![Output]({{ "images/child-product-data/child-product-data-output.png" }} "Product page with changed child data (e.g. breadcrumbs, title, SKU)")

## Requirements
- magento/framework: `~102.0||~103.0`
- magento/module-catalog: `~103.0||~104.0`
- magento/module-configurable-product: `~100.4`
- magento/module-eav: `~102.0`
- magento/module-store: `~101.0`
- php: `~7.4.0||~8.1.0||~8.2.0||~8.3.0`

## Compatibility
- Magento Open Source / Adobe Commerce >= `2.4`
- Hyv&auml; Themes >= `1.0.0`

## Installation Instructions
The installation procedure highly depends on your setup. In any case, you should use a version control system like git and test the installation on a development system.
If you are using composer (you should!) and downloaded the extension from the Marketplace or have set up your own composer repository, we recommend installing via composer.

### Composer Installation
1. `composer require customgento/module-child-product-data`
2. `bin/magento module:enable CustomGento_ChildProductData`
3. `bin/magento setup:upgrade`
4. `bin/magento setup:di:compile`
5. `bin/magento cache:flush`

### Manual Installation
1. unzip the downloaded files
2. create the directory `app/code/CustomGento/ChildProductData/`: `mkdir -p app/code/CustomGento/ChildProductData/`
3. copy the unzipped files to the newly created directory `app/code/CustomGento/ChildProductData/`
4. `bin/magento module:enable CustomGento_ChildProductData`
5. `bin/magento setup:upgrade`
6. `bin/magento setup:di:compile`
7. `bin/magento cache:flush`

## Troubleshooting - I installed the extension, but it does not work
1. Do you use the latest version of the extension?
2. Do you use Magento >= 2.4?

## Uninstallation
The uninstallation procedure depends on your setup:

### Uninstallation After Composer Installation
1. `bin/magento module:uninstall CustomGento_ChildProductData`
2. `bin/magento setup:di:compile`
3. `bin/magento cache:flush`

### Uninstallation After Manual Installation
1. `bin/magento module:disable CustomGento_ChildProductData`
2. `bin/magento setup:di:compile`
3. `bin/magento cache:flush`
4. `rm -r app/code/CustomGento/ChildProductData`

## Support
If you have any issues with this extension, feel free to [contact us](https://www.customgento.com/){:target="_blank"}!

## Licence
[CustomGento Commercial Software Licence](https://www.customgento.com/license){:target="_blank"}

## Copyright
&copy; 2023 - present CustomGento GmbH

