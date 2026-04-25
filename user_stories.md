
---

# User Stories

## Distribution Chain Streamlining System

---

## Overview

* This document describes the **end-to-end operational flow** of the system
* Focuses on:

  * Real business processes
  * Interaction between Admin, Staff, and Customers
* Covers the lifecycle from:

  * Supplier setup → Procurement → Inventory → Sales → Accounting → Settlement

---

## 1. Supplier and Product Setup (Admin)

### User Story

* As an **Admin**, I want to set up suppliers and products so that I can start procurement and sales operations.

### Flow

* Admin creates a new supplier

  * Inputs supplier details (name, contact, address)
* Admin creates products

  * Defines:

    * Product name
    * Unit of measure
    * MRP
* Admin ensures products are ready to be procured and sold

---

## 2. Stock Procurement (Admin)

### User Story

* As an **Admin**, I want to procure stock from suppliers so that inventory is available for sale.

### Flow

* Admin selects supplier
* Admin records procurement:

  * Product
  * Quantity
  * Cost per unit
* System:

  * Adds stock to inventory
  * Creates supplier ledger entry
* Admin chooses payment type:

  * Paid immediately
  * Credit (pay later)

---

## 3. Inventory Availability

### User Story

* As a **Staff member**, I want to view available stock so that I can confidently place orders.

### Flow

* Staff checks inventory

  * Views available quantities per product
* System ensures:

  * Real-time stock visibility

---

## 4. Customer Creation and Pricing (Staff)

### User Story

* As a **Staff member**, I want to create customers and assign pricing so that I can sell products to them.

### Flow

* Staff creates a new customer

  * Adds business details and contact information
* Staff defines price list for that customer

  * Selects products
  * Assigns agreed price per product

---

## 5. Order Placement (Staff)

### User Story

* As a **Staff member**, I want to place orders on behalf of customers so that sales can be recorded.

### Flow

* Staff selects customer
* Adds products and quantities
* System:

  * Applies customer-specific pricing
  * Calculates total order value
* Order is created with status: **Created**

---

## 6. Order Processing and Delivery (Staff)

### User Story

* As a **Staff member**, I want to update order status so that delivery progress is tracked.

### Flow

* Staff updates order status:

  * Created → Confirmed → Ready → Delivered
* Upon delivery:

  * System:

    * Deducts inventory
    * Marks order as completed
    * Prepares for invoicing

---

## 7. Invoice Generation (Admin)

### User Story

* As an **Admin**, I want to generate invoices so that I can formally request payment from customers.

### Flow

* Admin generates invoice:

  * Based on delivered orders
  * For a date range or specific order(s)
* Invoice includes:

  * Product details
  * Quantities
  * Prices
  * Total amount
* System:

  * Creates ledger entry (debit)
  * Updates customer outstanding balance
* Invoice is shared with customer

---

## 8. Customer Account Tracking (Admin)

### User Story

* As an **Admin**, I want to view customer accounts so that I can track outstanding payments.

### Flow

* Admin opens customer ledger
* Views:

  * All invoices
  * All payments
  * Running balance
* Identifies:

  * Pending dues
  * Overdue amounts

---

## 9. Statement Generation (Admin)

### User Story

* As an **Admin**, I want to generate account statements so that I can provide customers with a complete financial summary.

### Flow

* Admin selects customer
* Selects date range (e.g., last month)
* System generates statement:

  * Opening balance
  * Invoices
  * Payments
  * Closing balance
* Statement is shared with customer as:

  * Payment request
  * Transaction proof

---

## 10. Payment Collection (Staff / Admin)

### User Story

* As a **Staff member or Admin**, I want to record customer payments so that accounts remain accurate.

### Flow

* Customer makes payment
* Staff/Admin records payment:

  * Amount
  * Date
  * Payment mode
* System:

  * Creates ledger entry (credit)
  * Updates outstanding balance

---

## 11. Receipt Generation (Admin)

### User Story

* As an **Admin**, I want to generate receipts so that customers have proof of payment.

### Flow

* After payment entry:

  * System generates receipt
* Receipt includes:

  * Payment details
  * Linked invoices (optional)
  * Remaining balance
* Receipt is shared with customer

---

## 12. Account Settlement

### User Story

* As an **Admin**, I want to settle customer accounts so that outstanding balances are cleared.

### Flow

* Admin verifies:

  * Total outstanding balance
* Customer pays full or partial amount
* System:

  * Updates ledger
  * Adjusts balance
* If fully paid:

  * Account shows zero balance
* If partial:

  * Remaining balance continues as outstanding

---

## 13. Supplier Payment Settlement (Admin)

### User Story

* As an **Admin**, I want to pay suppliers so that procurement relationships are maintained.

### Flow

* Admin views supplier ledger
* Identifies outstanding dues
* Records payment:

  * Amount
  * Date
* System:

  * Updates supplier balance
  * Records transaction

---

## 14. Continuous Business Cycle

### User Story

* As a **business owner**, I want a continuous operational loop so that my distribution chain runs smoothly.

### Flow Loop

* Procurement → Inventory → Customer Creation → Pricing → Orders → Delivery → Invoicing → Payment → Settlement → Repeat

---

## Key Outcome

* Complete visibility into:

  * Stock
  * Sales
  * Customer balances
  * Supplier balances
* Seamless integration between:

  * Operations and accounting
* Reduced manual tracking and errors

---
