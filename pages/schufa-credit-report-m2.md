---
title: SCHUFA Credit Report (Magento 2)
permalink: schufa-credit-report-m2.html
summary: "The SCHUFA Credit Report module for Magento 2 allows you to check the creditworthiness of your customers in order to
allow / block certain payment methods."
sidebar: scr_m2_sidebar
toc: false
---

## Description

This module checks the customer's SCHUFA score in the checkout page and then decides whether to allow or
block certain payment methods based on the score, and then If the payment method is blocked, the customer will see a message
explaining the reason for blocking the payment method, after that the payment method option will be hidden, for the customer, and this blocked payment method will not be available for the customer to choose.
this data is saved in the user's cookie, so the customer can see the payment method if he/she clears the cookies.
The module uses the SCHUFA API to get the score and the report. There are also some configuration options to define the
score threshold and the payment methods to block.

**The module also works with Hyv&auml; Checkout.**

## Requirements

- ext-curl: `*`,
- magento/framework `^103.0`
- magento/module-checkout `^100.4`
- magento/module-payment `^100.4`
- PHP `~8.1.0||~8.2.0||~8.3.0`

## Compatibility

- Magento Open Source / Adobe Commerce >= 2.4
- Hyv&auml; Checkout >= 1.1.23

## Installation Instructions

The installation procedure highly depends on your setup. In any case, you should use a version control system like git
and test the installation on a development system.
If you are using composer (you should!) and downloaded the extension from the Marketplace or have set up your own
composer repository, we recommend installing via composer.

### Composer Installation

1. `composer require customgento/module-schufa-credit-report-m2`
2. `bin/magento module:enable CustomGento_SchufaCreditReport`
3. `bin/magento setup:upgrade`
4. `bin/magento setup:di:compile`
5. `bin/magento cache:flush`

### Manual Installation

1. unzip the downloaded files
2. create the directory `app/code/CustomGento/SchufaCreditReport/`:
   `mkdir -p app/code/CustomGento/SchufaCreditReport/`
3. copy the unzipped files to the newly created directory `app/code/CustomGento/SchufaCreditReport/`
4. `bin/magento module:enable CustomGento_SchufaCreditReport`
5. `bin/magento setup:upgrade`
6. `bin/magento setup:di:compile`
7. `bin/magento cache:flush`

## Configuration

You find the settings under Stores > Configuration > Sales > SCHUFA.
There are two groups of configurations General and Rules. In `General` group you can enable the extension and set the API credentials.
and in the `Rules` group you can set the score threshold and the payment methods to block.

![Configure General Settings for SCHUFA Credit Report]({{ "
images/schufa-credit-report-m2/general-group.png" }} "Configure General Settings for SCHUFA Credit Report")

- **Enable** Enable or disable the extension.
- **Test/Live** Enable or disable the test mode.
- **Client Id** SCHUFA client id.
- **Client Certificate** The content of the Certificate file.
- **Client Key** The content of the key file.

Now we need to define some rules for payment methods.

![Rules configuration for SCHUFA Credit Report module]({{ "
images/schufa-credit-report-m2/rules-group.png" }} "Rules configuration for SCHUFA Credit Report module")

- **Minimum Order Value** The module just checks the score if the order value is greater than this value.
- **Maximum Number Of Failed Credit Reports** Enable or disable the test mode.
- **Require Verified Identity** Whether the customer's identity should be verified.
- **Payment** We can define which payment methods should be checked by the module. as you can see it is a repetitive field, so you can add as many payment methods as you want.
- - **Payment Method** The payment method name to check.
- - **Rating Level/ Risk Ratio** The minimum score to allow the payment method.
- - **Maximum Order Total** The maximum order total to allow the payment method.

## Troubleshooting - I installed the extension, but it does not work

1. Do you use the latest version of the extension?
2. Do you use Magento >= 2.4?
3. Do you really use the correct SCHUFA API credentials?
4. Are you using the correct certification files?
5. Make sure to test it in incognito mode or clear the cache.
6. Make sure that the extension is **not** disabled under Stores > Configuration > Sales > SCHUFA.
7. Make sure that the SCHUFA Credit Report is enabled in the payment methods configuration.

## Uninstallation

The uninstallation procedure depends on your setup:

### Uninstallation After Composer Installation

1. `bin/magento module:uninstall CustomGento_SchufaCreditReport`
2. `bin/magento setup:di:compile`
3. `bin/magento cache:flush`

### Uninstallation After Manual Installation

1. `bin/magento module:disable CustomGento_SchufaCreditReport`
2. `bin/magento setup:di:compile`
3. `bin/magento cache:flush`
4. `rm -r app/code/CustomGento/SchufaCreditReport`

## Support

If you have any issues with this extension, feel free to [contact us](https://www.customgento.com/){:target="_blank"}!

## Licence

[CustomGento Commercial Software Licence](https://www.customgento.com/license){:target="_blank"}

## Copyright

&copy; 2024 - present CustomGento GmbH
