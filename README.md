# HandsMen Threads - Capstone Project 👔

## Project Overview
HandsMen Threads is a Salesforce solution designed to optimize men's fashion retail operations. The system automates inventory management, order processing, and customer loyalty programs.

**Tech Stack:** Apex Triggers, Schedulable Apex, Email Templates, Data Modeling.

## Key Automation Features

### 1. Auto-Calculation of Order Total 💰
**Trigger:** `OrderTotalTrigger`
- Automatically calculates the `Total_Amount__c` on an Order record based on the Product Price and Quantity selected.
- Ensures financial data accuracy before the record is saved.

### 2. Automatic Stock Deduction 📉
**Trigger:** `StockDeductionTrigger`
- Listens for changes in Order Status.
- When an Order is set to **'Confirmed'**, the system automatically deducts the ordered quantity from the `Inventory__c` object.
- Prevents selling out-of-stock items manually.

### 3. Scheduled Inventory Sync ⏰
**Class:** `InventoryBatchJob`
- A Schedulable Apex class designed to run nightly.
- **Schedule Code:** `System.schedule('Daily Inventory Sync', '0 0 0 * * ?', new InventoryBatchJob());`

### 4. Customer Communication 📧
- **Order Confirmation:** Automated email sent upon order confirmation.
- **Low Stock Alert:** Internal alert to the Inventory Manager when stock runs low.
- **Loyalty Program:** Notifies customers when they reach a new tier (Silver/Gold/Platinum).

## How to Deploy
1. Deploy the `classes` and `triggers` folder to your Salesforce Org.
2. Setup the Email Templates using the text provided in `documentation/email_templates.txt`.
3. Run the Anonymous Apex script to schedule the nightly job.
