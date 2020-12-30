---
title: Tier Prices For Configurable Products (Magento 2)
permalink: tier-prices-for-configurable-products-m2.html
summary: "The extension Tier Prices For Configurable Products or CustomGento_ConfigurableTierPrices changes the way Magento calculates tier prices of configurable products. This extension ensures that when you add different variations of a configurable product to the cart, you receive the tier price for the total quantity of all variations in the cart."
sidebar: ctp_m2_sidebar
toc: false
---

## Description
This extension for Magento 2 changes the way Magento calculates tier prices of configurable products. You can add different variations of a configurable product to the cart and you will receive the tier price for the total quantity of all variations in the cart.

### Example
There is a configurable product "Awesome T-Shirt" and there are two corresponding variations "green" and "orange".
The price for each t-shirt is 20 USD.
If you buy five or more green ones, you only have to pay 18 USD each.
If you buy five or more of the orange ones, you only have to pay 16 USD each.
Now you add three green and two orange t-shirts to your cart.
What would you expect? You would like to have the t-shirts for 16 USD each or at least for 18 USD each, right?
Not with Magento. Unfortunately, Magento will charge you 20 USD each:

![Tier Prices Without CustomGento_ConfigurableTierPrices]({{ "images/tier-prices-for-configurable-products-m2/tier-prices-before.png" }} "Tier Prices Without CustomGento_ConfigurableTierPrices")

Fortunately, you can install the module Tier Prices For Configurable Products and even decide if the highest, 
the lowest or the respective tier price of the product should be charged.

If you configure the extension to charge the highest tier price, you get the t-shirts for 18 USD each:

![Tier Prices With CustomGento_ConfigurableTierPrices - Highest Tier Price]({{ "images/tier-prices-for-configurable-products-m2/tier-prices-after-highest.png" }} "Tier Prices With CustomGento_ConfigurableTierPrices")

If you configure the extension to charge the lowest tier price, you get the t-shirts for 16 USD each:

![Tier Prices With CustomGento_ConfigurableTierPrices - Lowest Tier Price]({{ "images/tier-prices-for-configurable-products-m2/tier-prices-after-lowest.png" }} "Tier Prices With CustomGento_ConfigurableTierPrices")

And you can even configure that the respective tier prices should be charged.
In this case, you get the green ones for 18 USD each and the orange ones for 16 USD each.

![Tier Prices With CustomGento_ConfigurableTierPrices - Respective Tier Price]({{ "images/tier-prices-for-configurable-products-m2/tier-prices-after-respective.png" }} "Tier Prices With CustomGento_ConfigurableTierPrices")

### Simple Products Visible In Catalog
Given your simple products, which are assigned to configurable products, are also visible in the catalog individually: If the customer adds such simple products to the cart plus their respective configurable counterparts, both quantities will be combined and respected for the tier price calculation. 

## Requirements
- PHP `~7.2.0||~7.3.0||~7.4.0`
- magento/framework `~102.0.0||~103.0.0`
- magento/module-backend `~101.0||~102.0`
- magento/module-catalog `~103.0||~104.0`
- magento/module-checkout `~100.3`
- magento/module-configurable-product `~100.3`
- magento/module-customer: `~102.0||~103.0`
- magento/module-eav `~102.0`
- magento/module-quote `~101.0`
- magento/module-store `~101.0`

## Compatibility
- Magento >= 2.3

## Installation Instructions
The installation procedure highly depends on your setup. In any case, you should use a version control system like git and test the installation on a development system.
If you are using composer (you should!) and downloaded the extension from the Marketplace or have set up your own composer repository, we recommend installing via composer.

### Composer Installation
1. `composer require customgento/module-configurable-tier-prices-m2`
2. `bin/magento module:enable CustomGento_ConfigurableTierPrices`
3. `bin/magento setup:upgrade`
4. `bin/magento setup:di:compile`
5. `bin/magento cache:flush`

### Manual Installation
1. unzip the downloaded files
2. create the directory `app/code/CustomGento/ConfigurableTierPrices/`: `mkdir -p app/code/CustomGento/ConfigurableTierPrices/`
3. copy the unzipped files to the newly created directory `app/code/CustomGento/ConfigurableTierPrices/`
4. `bin/magento module:enable CustomGento_ConfigurableTierPrices`
5. `bin/magento setup:upgrade`
6. `bin/magento setup:di:compile`
7. `bin/magento cache:flush`

## Configuration
You find the settings under Stores > Configuration > Sales > Sales > Tier Prices For Configurable Products.
You can enable the extension there and choose the tier price calculation type:

![Configure Tier Prices For Configurable Products]({{ "images/tier-prices-for-configurable-products-m2/system-configuration.png" }} "Configure Tier Prices For Configurable Products")

Additionally it is possible to define specific product attributes, which should be handled differently in the calculation process.
When simple products in the cart differ in one of the chosen attributes, their qty is not summed up to calculate the tier prices.
To see the benefit of this feature, let's take the example of a configurable product with attributes color and size and the following children: 

- 10ml/red: 10 USD → 2 for 8 USD each
- 10ml/blue: 10 USD → 2 for 8 USD each
- 100ml/red: 100 USD → 2 for 80 USD each
- 100ml/blue: 100 USD → 2 for 80 USD each

When a customer now buys one unit of 10ml and one of 100ml, the quantities would be summed up and the tier price would be calculated according to the chosen calculation type. So if type `lowest` is used, the customer would get the products for 8 USD each, which is a lot too cheap for the 100ml product.
To prevent this, just choose `size` as ignored attribute and the extended calculation process will only apply to products with the same size.

It is also possible to disable the updated price calculation for specific categories or products.
Therefore, you can set the attribute `configurabletierprice_disabled` / "Disable Tier Prices For Configurable Products" to "Yes" in the configurable product or the category respectively.

Disable Tier Prices For Configurable Products in the configurable product:

![Disable Tier Prices For Configurable Products By Product]({{ "images/tier-prices-for-configurable-products-m2/disable-by-product.png" }} "Disable Tier Prices For Configurable Products By Category")

Disable Tier Prices For Configurable Products in the category:

![Disable Tier Prices For Configurable Products By Category]({{ "images/tier-prices-for-configurable-products-m2/disable-by-category.png" }} "Disable Tier Prices For Configurable Products By Category")

If Tier Prices For Configurable Products is disabled for a specific product or for any category this product is assigned to, the extension will not change the price calculation of this product at all.
Please note, that in this case the original Magento price calculation will work as usual. Tier prices will still be applied, if the required quantity of a child product is reached, but the quantities
will not be summed up anymore between different child products. 

## Troubleshooting - I installed the extension, but it does not work
1. Do you use the latest version of the extension?
2. Do you use Magento >= 2.3?
3. Do you really use configurable products? This extension only works with configurable products. It does not work if you use e.g. simple products with custom options.
4. Make sure that the extension is **not** disabled under Stores > Configuration > Sales > Sales > Tier Prices For Configurable Products.
5. Make sure that the configurable product is **not** in one of the disabled categories.
6. Make sure that the extension is **not** disabled in the respective configurable product.
7. Make sure that your tier prices are lower than the normal prices. That is the way they are supposed to be used.

## Uninstallation
The installation procedure depends on your setup:

### Uninstallation After Composer Installation
1. `bin/magento module:uninstall CustomGento_ConfigurableTierPrices`
2. `bin/magento setup:di:compile`
3. `bin/magento cache:flush`

### Uninstallation After Manual Installation
1. `bin/magento module:disable CustomGento_ConfigurableTierPrices`
2. `bin/magento setup:di:compile`
3. `bin/magento cache:flush`
4. `rm -r app/code/CustomGento/ConfigurableTierPrices`

## Support
If you have any issues with this extension, feel free to [contact us](https://www.customgento.com/){:target="_blank"}!

## Licence
[CustomGento Commercial Software Licence](https://www.customgento.com/license){:target="_blank"}

## Copyright
(c) 2018-2020 CustomGento / Simon Sprankel
