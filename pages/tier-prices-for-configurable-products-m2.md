---
title: Tier Prices For Configurable Products (Magento 2)
permalink: tier-prices-for-configurable-products-m2.html
summary: "The extension Tier Prices For Configurable Products or CustomGento_ConfigurableTierPrices changes the way Magento calculates tier prices of configurable products. This extension ensures that when you add different variations of a configurable product to the cart, you receive the tier price for the total quantity of all variations in the cart."
sidebar: ctp2_sidebar
---

## Description
This extension for Magento 2 changes the way Magento calculates tier prices of configurable products. You can add different variations of a configurable product to the cart and you will receive the tier price for the total quantity of all variations in the cart.

### Example
There is a configurable product "Awesome T-Shirt" and there are two corresponding variations "green" and "orange". 
The price for each t-shirt is 20 US-Dollar. 
If you buy five or more green ones, you only have to pay 18 US-Dollar each. 
If you buy five or more of the orange ones, you only have to pay 16 US-Dollar each. 
Now you add three green and two orange t-shirts to your cart. 
What would you expect? You would like to have the t-shirts for 16 US-Dollar each or at least for 18 US-Dollar each, right?
Not with Magento. Unfortunately, Magento will charge you 20 US-Dollar each:

![Tier Prices Without CustomGento_ConfigurableTierPrices]({{ "images/tier-prices-for-configurable-products-m2/tier-prices-before.png" }} "Tier Prices Without CustomGento_ConfigurableTierPrices")

Fortunately, you can install the module Tier Prices For Configurable Products and even decide if the highest, 
the lowest or the respective tier price of the product shall be charged.

If the highest price is charged, you get the t-shirts for 18 US-Dollar each:

![Tier Prices With CustomGento_ConfigurableTierPrices]({{ "images/tier-prices-for-configurable-products-m2/tier-prices-after-highest.png" }} "Tier Prices With CustomGento_ConfigurableTierPrices")

If the lowest price is charged, you get the t-shirts for 16 US-Dollar each:

![Tier Prices With CustomGento_ConfigurableTierPrices]({{ "images/tier-prices-for-configurable-products-m2/tier-prices-after-lowest.png" }} "Tier Prices With CustomGento_ConfigurableTierPrices")

And you can even choose that the respective tier prices shall be taken. So you for the green ones 18 US-Dollar each and for the orange ones 16 US-Dollar each respectively.

![Tier Prices With CustomGento_ConfigurableTierPrices]({{ "images/tier-prices-for-configurable-products-m2/tier-prices-after-respective.png" }} "Tier Prices With CustomGento_ConfigurableTierPrices")


## Requirements
- PHP >= 7.0
- magento/module-catalog
- magento/module-eav
- magento/module-store
- magento/module-backend
- magento/framework

## Compatibility
- Magento >= 2.2

## Installation Instructions
// TODO

## Configuration
You find the settings under Stores > Configuration > Sales > Sales > Configurable Tier Prices.
You can enable the extension there and also choose the tier price calculation type.

![Configure Tier Prices For Configurable Products]({{ "images/tier-prices-for-configurable-products-m2/system-configuration.png" }} "Configure Tier Prices For Configurable Products")

It is also possible to disable the updated price calculation for specific categories or products.
Therefore, you can set the attribute `configurabletierprice_disabled` / " Disable Configurable Tier Prices" in the top section of the configurable product respectively the category to "Yes":

![Disable Tier Prices For Configurable Products By Category]({{ "images/tier-prices-for-configurable-products-m2/disable-by-category.png" }} "Disable Tier Prices For Configurable Products By Category")
  
## Troubleshooting - I installed the extension, but it does not work

1. Do you use the latest version of the extension?
2. Do you really use configurable products? This extension only works with configurable products. It does not work if you use e.g. simple products with custom options.
3. Make sure that the extension is **not**  disabled under Stores > Configuration > Sales > Sales > Configurable Tier Prices.
4. Make sure that the configurable product is **not** in one of the disabled categories.
5. Make sure that the extension is **not**  disabled in the respective configurable product.
6. Make sure that your tier prices are lower than the normal prices. That is the way they are supposed to be used.

## Uninstallation
// TODO

## Support
If you have any issues with this extension, feel free to [contact us](http://customgento.com/)!

## Licence
[OSL - Open Software Licence 3.0](https://opensource.org/licenses/osl-3.0.php)

## Copyright
(c) 2012-2017 CustomGento / Simon Sprankel
