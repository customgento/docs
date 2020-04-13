---
title: Tier Prices For Configurable Products (Magento 1)
permalink: tier-prices-for-configurable-products-m1.html
summary: "The extension Tier Prices For Configurable Products or CustomGento_ConfigurableTierPrices &ndash; formerly known as Spranks_ConfigurableTierPrices &ndash; changes the way Magento calculates tier prices of configurable products. This extension ensures that when you add different variations of a configurable product to the cart, you receive the tier price for the total quantity of all variations in the cart."
sidebar: ctp_m1_sidebar
---

## Description
This extension for Magento 1 changes the way Magento calculates tier prices of configurable products. You can add different variations of a configurable product to the cart and you will receive the tier price for the total quantity of all variations in the cart.

### Example
There is a configurable product "Awesome T-Shirt" and there are two corresponding variations "green" and "orange". The price for each t-shirt is 20 EUR. If you buy five or more, you only have to pay 18 EUR each. Now you add three green and two orange t-shirts to your cart. What would you expect? You would like to have the t-shirts for 18 EUR each, right? Not with Magento. Unfortunately, Magento will charge you 20 EUR each:

![Tier Prices Without CustomGento_ConfigurableTierPrices]({{ "images/tier-prices-for-configurable-products-m1/tier-prices-before.png" }} "Tier Prices Without CustomGento_ConfigurableTierPrices")

Fortunately, you can install the module Tier Prices For Configurable Products and 18 EUR will be charged as expected:

![Tier Prices With CustomGento_ConfigurableTierPrices]({{ "images/tier-prices-for-configurable-products-m1/tier-prices-after.png" }} "Tier Prices With CustomGento_ConfigurableTierPrices")

## Requirements
- PHP >= 5.5.0
- Mage_Catalog
- Mage_Checkout
- Mage_Core
- Mage_Sales

## Compatibility
- Magento >= 1.7 and < 2.0

## Installation Instructions
1. If you have installed Spranks_ConfigurableTierPrices before, please delete the following files and folders from your Magento root before you install this extension:
    - app/etc/modules/Spranks_ConfigurableTierPrices.xml
    - app/code/local/Spranks/ConfigurableTierPrices
    - app/code/community/Spranks/ConfigurableTierPrices
2. Copy all the files into your document root.
3. Clear the cache.

For more in-depth Magento extension installation instructions, checkout [Fooman's Ultimate Guide to Installing Magento Extensions](https://store.fooman.co.nz/media/custom/upload/TheUltimateGuidetoInstallingMagentoExtensions.pdf){:target="_blank"}.

## Configuration
You find the settings under System > Configuration > Sales > Tier Prices For Configurable Products.
You can enable the extension there. You can disable the extension for specific categories as well.
If you want to disable the extension for multiple categories, hold down CTRL and select all respective categories:

![Configure Tier Prices For Configurable Products]({{ "images/tier-prices-for-configurable-products-m1/system-configuration.png" }} "Configure Tier Prices For Configurable Products")

It is also possible to disable the updated price calculation for specific products.
Therefore, you can set the attribute `configtierprices_disabled` / "Disable Tier Prices For Configurable Products" in the "General" tab of the product to "Yes":

![Disable Tier Prices For Configurable Products By Product]({{ "images/tier-prices-for-configurable-products-m1/disable-by-product.png" }} "Disable Tier Prices For Configurable Products By Product")
  
## Troubleshooting - I installed the extension, but it does not work

1. Do you use the latest version of the extension?
2. Do you use Magento >= 1.7?
3. Do you really use configurable products? This extension only works with configurable products. It does not work if you use e.g. simple products with custom options.
4. Make sure that the extension is not disabled under System > Configuration > Sales > Tier Prices For Configurable Products.
5. Make sure that the configurable product is **not** in one of the disabled categories under System > Configuration > Sales > Tier Prices For Configurable Products.
6. Make sure that the extension is not disabled in the respective configurable product.
7. Make sure that your tier prices are lower than the normal prices. That is the way they are supposed to be used.

## Uninstallation
1. Remove all extension files from your Magento installation.
2. Clear the cache.
3. Run the following SQL query **after** removing the extension files:

```sql
DELETE FROM `eav_attribute` WHERE attribute_code = 'configtierprices_disabled';
DELETE FROM `core_resource` WHERE code = 'customgento_configurabletierprices_setup';
```

## Support
If you have any issues with this extension, open an issue on [GitHub](https://github.com/customgento/CustomGento_ConfigurableTierPrices/issues){:target="_blank"}.

## Travis Build Status
[![Build Status](https://travis-ci.org/customgento/CustomGento_ConfigurableTierPrices.svg?branch=master)](https://travis-ci.org/customgento/CustomGento_ConfigurableTierPrices){:target="_blank"}

## Contribution
Any contribution is highly appreciated. The best way to contribute code is to open a [pull request on GitHub](https://help.github.com/articles/using-pull-requests){:target="_blank"}.

## Licence
[OSL - Open Software Licence 3.0](https://opensource.org/licenses/osl-3.0.php){:target="_blank"}

## Copyright
(c) 2012-2020 CustomGento / Simon Sprankel
