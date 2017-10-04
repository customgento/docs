---
title: CustomGento_BankIntegration Documentation
permalink: bi_index.html
summary: "CustomGento Bankintegration helps you to save yourself a lot of time by importing bank data right into your Magento system. The module is designed for shops who provide prepayment or payment via invoice. Without CustomGento Bankintegration you had to check your bank statements, find the associated order in Magento and change the order status manually. Now all these steps are done automatically. You just upload your bank statement and the module finds the corresponding order via amount and order or invoice id and changes the status. This gives you a lot of time which you can use for the real important things in your business."
sidebar: bi_sidebar
---

## General Configuration
To configure CustomGento Bankintegration go to Configuration under the tab System. In the left menu you will find the item Customgento with the tab Bankintegration.
First of all you choose the banks you want to import your data from. You can choose several banks if you have more than one account. If your bank is not in the list, please contact us via info@customgento.com and send us an example of your bank statement format. We will then add your bank as soon as possible.
In the next section you decide the order status mapping. On the left side you choose for which status the module should check and on the right side you choose which status should be assigned if the relevant order has been paid. Of course you can choose various status combinations if needed. Please make sure that you do not create any logical conflicts between the different status mappings.
The next option is just relevant for users who use the M2E Pro module for synchronizing Magento with other marketplaces like Ebay or Amazon. These marketplaces have their own order ids. So the module has no chance to couple a bank entry to the right Magento order if the buyer just named the marketplace order id. If you enable this option, the module checks for these order ids and translates them into Magento order ids to find the right order.

In the following sections, you will find explanations for the use of each of the pages of the module. In short, the functionality of the module is as follows:

1. The user uploads a bank file to the module (see: The upload page).
2. The bank data is parsed and processed by the module. This includes the extraction of an order identifier from the data. The data is made available from within Magento. Duplicate entries are filtered out automatically.
3. The module performs the matching process to Magento orders (see: The bank/order coupling page):
    1. Extract a Magento order identifier or the IBAN (in case that the Itabs_Debit module is active) from one of the fields (fixed per bank) of the bank file.
    2. Calculate the open order amount for each open Magento order in case that a part of the total sum has already been payed or a creditmemo has been created.
    3. If the order identifier and the order amount match, the coupling is set to Certain. It is also set to Certain, if the IBAN and the amount match. If both tries faile, the module checks for the order amount and the name of the sender. If these match an existing order, the coupling is also set to Certain.
    4. If only the amount, the identifier or the name match, the coupling is set to Guess. All guessed bank items can be reviewed and set to Certain manually.
    5. Otherwise, the coupling has to be performed manually.

Furthermore, the module provides options to review bankdata (see: The bank payments tab and The review bankdata pages) and filter out entries automatically.
All of the following pages and tabs are shown under the general tab Bank Integration in your Magento backend.

## The Upload Page
On the upload page, you will find the banks you selected in the Configuration.
On this page, you can select a bank file to be uploaded and processed into Magento’s system (Choose File → Upload and process (xx)).

## The Bank/Order Coupling Page
On this page you will find an overview of unprocessed bankdata. If the overview contains rows marked as Uncoupled, you can try to couple them automatically using the Couple automatically button. After automatic coupling, the Coupling certainty of the bankdata can change in either Certain or Guess. Rows which are marked as Guess can either be decoupled (Decouple) or confirmed (Confirm).
Orders that remain Uncoupled can either be ignored (Ignore) or manually coupled.
For this you will find a list of orders with the order identifiers, customer names, and the total amount, so you can select the right one.
Using the Submit coupled data button will confirm the coupling of all bankdata marked as Certain, including the change of order status.

## The Review Bankdata Pages
On the review bankdata pages, you can see the results of the imported bank files. You can either see all data (All items), those already coupled (Processed items), those still open to process (Unprocessed items), or the ignored data (Ignored items). On these pages, you can perform various tasks:

* Add manual payment allows you to manually add a new entry, without importing this from a bank file.
* The action Export selected entries allow you to export the bankdata back to a comma separated values (CSV) file. This can be useful for your own bank administration.
* The actions Delete selected entries will remove bank entries from the Magento data-base. They can be re-added by uploading the bank data again. These options are recommended for debug/testing purposes only. Instead, we recommend to ignore unwanted bank entries.
* On the Ignored items page, ignored data can be un-ignored (Accept). This includes data filtered out automatically by the filters (see Filter settings).
* On the Processed items page, coupled data can be un-coupled (Decouple). This reverses the coupling process so you can select another order to asign. Please note, that the order status is not reversed, as this is impossible for several statuses according to Magento logic.

## The Bank Payments Tab
On the bank payments tab you will have an overview of all transactions made to a single order. This gives you a perorder overview of processed bankdata.

## The Filter Settings
On the filter settings page you can add, remove, or edit filters. These filters allow you to automatically filter out entries from imported bankdata. The bankdata matching these filters will not be removed, but will be marked automatically as Neglected and can thus be reviewed and re-added under Ignored items.
Using the Add new button or clicking on one of the existing filters allows you to add or modify a filter as follows:

* Under Name of the filter fill in a description. In this example, we create a filter to automatically neglect the monthly office rent.
* Under Field to filter, select one of the bankdata fields on which to apply the filter. The fields correspond to the columns shown in the Review bankdata pages. In this example, we know that the office rent is always paid from a fixed account number.
* Under Text to filter, we fill in the text we want to filter out. In this example, we fill in the account number to which we pay the office rent.
* Under Complete or partial string, we select either Exact or Partial. In this example, we select Exact, which means that the account number should contain the given number exactly: there must be no trailing or leading digits or characters.

## Frequently Asked Questions

