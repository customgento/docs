---
title: Tier Prices For Configurable Products
permalink: ctp_index.html
summary: "The extension Tier Prices For Configurable Products &ndash; formerly known as Spranks_ConfigurableTierPrices &ndash; changes the way Magento calculates tier prices of configurable products. You can now add different variants of a configurable product to the cart and you will get the tier price for the total quantity of all variants in the cart."
sidebar: ctp_sidebar
folder: ctp
---

## Description
This Magento module changes the way Magento calculates tier prices of configurable products. You can now add different variants of a configurable product to the cart and you will get the tier price for the total quantity of all variants in the cart.
Example: There is a configurable product "football" and there are two corresponding variants "white" and "orange". The price for each football is 20 EUR. If you buy five or more, you only have to pay 18 EUR each. Now you add three white and two orange footballs to your cart. What would you expect? You would like to have the footballs for 18 EUR each, right? Not with Magento. Unfortunately, Magento will charge you 20 EUR each. Fortunately, you can install the module Tier Prices For Configurable Products and 18 EUR will be charged as expected.

## Requirements
- PHP >= 5.5.0
- Mage_Catalog
- Mage_Checkout
- Mage_Core
- Mage_Sales

## Compatibility
- Magento >= 1.7

## Installation Instructions
1. If you have installed Tier Prices For Configurable Products before, please delete the following files and folders from your Magento root before you install this extension:
    - app/etc/modules/CustomGento_ConfigurableTierPrices.xml
    - app/code/local/CustomGento/ConfigurableTierPrices
2. Install the extension via Magento Connect with the key shown above or copy all the files into your document root.
3. Clear the cache.

## Setup Instructions
In your store config you find the settings for Tier Prices For Configurable Products under System - Configuration - Sales - Configurable Tier Prices.
There you can enable or disable the extension in general or for specific categories.
It is also possible to disable the price calculation for a specific product. 
You find an attribute for that in the general page of the product edit page.

## Functionality

Tier Prices For Configurable Products only changes the price of a configurable product if all of the following conditions are true:
- the extension is enabled under under System - Configuration - Sales - Configurable Tier Prices
- the configurable product is**not**in one of the selected categories under the same config path
- Tier Prices For Configurable Products is not disabled on the product edit page for the relevant configurable product
  
This way it is possible to adapt the extension according to your own needs and disable it for an individual selection of products.  
  
## Frequently Asked Questions 

### I installed the extension, but it does not work - can you help me?
Please check the following:

1. Do you use the latest version of the extension? If so, make sure you also use Magento >= 1.7.
2. Do you really use configurable products? This extension only works with configurable products. It does not work if you use e.g. simple products with custom options.
3. Make sure that the extension is not deactivated completely, for a specific category or for a specific product. You can check that under System - Configuration - Sales - Configurable Tier Prices or in the product respecively.
4. Make sure that your tier prices are lower than the normal prices. That is the way they are supposed to be used.

## Uninstallation
1. Remove all extension files from your Magento installation or uninstall the extension via Magento Connect.
2. Run the following SQL query after removing the extension files:

```sql
DELETE FROM `eav_attribute` WHERE attribute_code = 'configtierprices_disabled';
DELETE FROM `core_resource` WHERE code = 'customgento_configurabletierprices_setup';
```

## Support
If you have any issues with this extension, open an issue on [GitHub](https://github.com/customgento/CustomGento_ConfigurableTierPrices/issues).

## Travis Build Status
[![Build Status](https://travis-ci.org/customgento/CustomGento_ConfigurableTierPrices.svg?branch=master)](https://travis-ci.org/customgento/CustomGento_ConfigurableTierPrices)

## Contribution
Any contribution is highly appreciated. The best way to contribute code is to open a [pull request on GitHub](https://help.github.com/articles/using-pull-requests).

## Licence
[OSL - Open Software Licence 3.0](https://opensource.org/licenses/osl-3.0.php)

## Copyright
(c) 2012-2017 CustomGento / Simon Sprankel
