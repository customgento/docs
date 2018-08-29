---
title: Product Badges (Magento 1)
permalink: product-badges-m1.html
summary: "Product Badges for Magento 1 offers you the possibility to add customized badges to your product images. 
You can customize design, text and spot for your badge. It is also possible to filter the products where the badge should be shown."
sidebar: pb_m1_sidebar
---

## Description
Product Badges for Magento 1 offers you the possibility to add customized badges to your product images. 
You can customize design, text and spot for your badge. 
It is also possible to filter the products where the badge should be shown.

### Example
To show how extremly customizable Product Badges is, you see below an example, where we chose several conditions to our
different badges. We added one badge for all virtual products, one for all configurables, one for all products and one for 
just the green ones.
Like this you can add as many badges as you want and choose for every badge the fitting conditions.

![Example]({{ "images/product-badges-m1/example.png" }} "Example")


## Requirements
- PHP >= 5.5.0
- Mage_Catalog
- Mage_Core

## Compatibility
- Magento >= 1.7 and <= 2.0

## Installation Instructions
1. Copy all the files into your document root.
2. Clear the cache.

For more in-depth Magento extension installation instructions, checkout [Fooman's Ultimate Guide to Installing Magento Extensions](https://store.fooman.co.nz/media/custom/upload/TheUltimateGuidetoInstallingMagentoExtensions.pdf).

## Configuration
You find the settings under System > Configuration > Catalog > Product Badges.

![System Configuration for Product Badges]({{ "images/product-badges-m1/system-configuration.png" }} "System Configuration for Product Badges")

You can enable the extension there and also decide if th reindex should be run after every save of a badge.
To create new badges or edit existing ones, go to Catalog > Product Badges.
With a click on 'Add new Badge' you find a form where you can input all required data like name, internal code and internal description.

![Adding a new badge]({{ "images/product-badges-m1/add-new-badge.png" }} "Adding a new badge")

You can activate or inactivate a badge there. Right below you find a section for the visualisation settings.
There you can decide the shape of the badge, upload a customized image if you want, and choose the text, colour and spot for your badge.
On the left side you can switch to the next tab conditions and filter the products where your badge should be shown.

In general you have to add the following lines in the of catalog/product/list.phtml of your current theme:
```php
/** @var CustomGento_ProductBadges_Helper_Data $_badgesHelper */
$_badgesHelper = Mage::helper('customgento_productbadges');
$_badgesHelper->initProductBadgeCollection($_productCollection);
```

Below list.phtml you have to add the actual code that renders the badges per products:
```php
<?php
    /**
     * Rendering product badges for Product List Page
     */
     echo $_badgesHelper->generateBadgesHtml($_product);
?>
```


## Troubleshooting - I installed the extension, but it does not work
1. Do you use the latest version of the extension?
2. Make sure that the extension is **not**  disabled under Stores > Configuration > Catalog > Product Badges.
3. Make sure that the automatic index is **not** disabled or if it is, reindex manually in the index management.
4. Check if you chose fitting conditions for your badge, so that it is displayed for the correct collection of products.

## Uninstallation
1. Remove all extension files from your Magento installation.
2. Clear the cache.
3. Run the following SQL query **after** removing the extension files:
```sql
DROP TABLE `customgento_productbadges_queue`;
DROP TABLE `customgento_productbadges_badges_config`;
DELETE FROM `core_resource` WHERE code = 'customgento_productbadges_setup';
```
4. Drop all tables matching the pattern `customgento_productbadges_badges_index_*`. The extension creates one table per store, so that the number of tables depends on your configuration.

## Support
If you have any issues with this extension, feel free to [contact us](https://www.customgento.com)!

## Licence
[CustomGento Commercial Software Licence](https://www.customgento.com/license){:target="_blank"}

## Copyright
(c) 2018 CustomGento / Simon Sprankel
