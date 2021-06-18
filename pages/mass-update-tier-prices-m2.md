---
title: Mass Update Tier Prices (Magento 2)
permalink: mass-update-tier-prices-m2.html
summary: "The extension Mass Update Tier Prices or CustomGento_MassUpdateTierPrices provides the ability to mass update tier prices for multiple products at once. You can replace already existing tier prices or simply add new ones to as many products you want with just one click instead of configuring each product individually."
sidebar: mutp_m2_sidebar
toc: false
---

## Description
This extension for Magento 2 provides the ability to mass update the tier prices for multiple products at once.

If you want to add the same tier prices to more than one product, you no longer need to configure each of those products (or in case of configurable products each variation) individually. Instead, you conveniently configure the tier prices at one place only and apply them to every product that should have them. You can choose whether the new tier prices should only complement or completely replace already existing ones. In case of configurable products, all variations get the new tier prices applied.

## Usage Instructions
In your product overview (Catalog > Products) select the products that should get new tier prices and choose Actions > Update attributes.

![Select Products]({{ "images/mass-update-tier-prices-m2/select-items.jpg" }} "Select Products")

![Choose Update Attributes]({{ "images/mass-update-tier-prices-m2/update-attribute.jpg" }} "Choose Update Attributes")

Select "Mass Update Tier Prices". Add and configure as many tier prices as needed. Make sure to uncheck the checkbox, if you do not wish to replace already existing tier prices of the products. If the products do not have tier prices attached yet, you can keep the checkbox checked. Hit "Save" when finished.

![Mass Update Tier Prices Extension]({{ "images/mass-update-tier-prices-m2/configure-rules-form.jpg" }} "Mass Update Tier Prices Extension")

![Configure The Tier Price Rules]({{ "images/mass-update-tier-prices-m2/configure-rules.jpg" }} "Configure The Tier Price Rules")

You will now be notified, that the tier price changes are scheduled for update and added to the queue. They get processed via the cronjob, which may take a few minutes, depending on your cronjob settings. You need to make sure, that your cronjob is running successfully (System > Tools > Cron Job Manager). You can check the status of the updates under System > Action Logs > Bulk Actions.

![Queue Notification]({{ "images/mass-update-tier-prices-m2/queue.jpg" }} "Queue Notification")

![Bulk Actions Log]({{ "images/mass-update-tier-prices-m2/bulk-actions-log.jpg" }} "Bulk Actions Log")

After the updates have been processed, go back to your product overview, open one of the altered products and navigate to "Advanced Pricing". The tier prices are applied now. If you chose a configurable product, the tier prices are automatically applied to all it's variations now.

![Tier Prices Applied To Product]({{ "images/mass-update-tier-prices-m2/check-product.jpg" }} "Tier Prices Applied To Product")

## Requirements
- PHP `~7.3.0||~7.4.0`
- magento/framework `~103.0.0`
- magento/module-asynchronous-operations `~100.4`
- magento/module-authorization `~100.4`
- magento/module-backend `~102.0`
- magento/module-catalog `~104.0`
- magento/module-customer: `~103.0`
- magento/module-directory `~100.4`
- magento/module-store `~101.0`
- magento/module-ui `~101.1`

## Compatibility
- Magento >= 2.4

## Installation Instructions
The installation procedure highly depends on your setup. In any case, you should use a version control system like git and test the installation on a development system.
If you are using composer (you should!) and downloaded the extension from the Marketplace or have set up your own composer repository, we recommend installing via composer.

### Composer Installation
1. `composer require customgento/module-mass-update-tier-prices-m2`
2. `bin/magento module:enable CustomGento_MassUpdateTierPrices`
3. `bin/magento setup:upgrade`
4. `bin/magento setup:di:compile`
5. `bin/magento cache:flush`

### Manual Installation
1. unzip the downloaded files
2. create the directory `app/code/CustomGento/MassUpdateTierPrices/`: `mkdir -p app/code/CustomGento/MassUpdateTierPrices/`
3. copy the unzipped files to the newly created directory `app/code/CustomGento/MassUpdateTierPrices/`
4. `bin/magento module:enable CustomGento_MassUpdateTierPrices`
5. `bin/magento setup:upgrade`
6. `bin/magento setup:di:compile`
7. `bin/magento cache:flush`

## Configuration
Conveniently, the extension is enabled by default. No configurations needed.

## Troubleshooting - I installed the extension, but it does not work
1. Do you use the latest version of the extension?
2. Do you use Magento >= 2.4?
7. Make sure that your tier prices are lower than the normal prices. That is the way they are supposed to be used.

## Uninstallation
The installation procedure depends on your setup:

### Uninstallation After Composer Installation
1. `bin/magento module:uninstall CustomGento_MassUpdateTierPrices`
2. `bin/magento setup:di:compile`
3. `bin/magento cache:flush`

### Uninstallation After Manual Installation
1. `bin/magento module:disable CustomGento_MassUpdateTierPrices`
2. `bin/magento setup:di:compile`
3. `bin/magento cache:flush`
4. `rm -r app/code/CustomGento/MassUpdateTierPrices`

## Support
If you have any issues with this extension, feel free to [contact us](https://www.customgento.com/){:target="_blank"}!

## Licence
[CustomGento Commercial Software Licence](https://www.customgento.com/license){:target="_blank"}

## Copyright
&copy; 2021 CustomGento GmbH
