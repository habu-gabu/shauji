---

# Distribution Chain Streamlining System

## Software Requirements Document (SRD)

---

## 1. Introduction

### 1.1 Purpose

* Define requirements for a distribution chain, inventory, and accounting system
* Streamline procurement, inventory tracking, sales, accounting, and reporting
* Provide full visibility into stock, costs, pricing, customer transactions, and financials

### 1.2 Scope

* Covers end-to-end operations:

  * Supplier procurement
  * Inventory management
  * Product tracking
  * Customer management
  * Order processing
  * Pricing management
  * Accounting and invoicing
  * Reporting and analytics
* Multi-user system with role-based access (admin and staff)
* Accounting is **fully integrated with customer management and order lifecycle**

---

## 2. User Roles

### 2.1 Admin

* Full system access
* Manage:

  * Products
  * Suppliers
  * Customers
  * Pricing
  * Accounting
* View reports and analytics
* Monitor financial health and operations

### 2.2 Staff (Field Agents)

* Create orders on behalf of customers
* Update delivery status
* View assigned customers and pricing
* Limited access to financial/accounting data (view-only where applicable)

---

## 3. Functional Requirements

---

## 3.1 Supplier Management

* Add, update, disable suppliers
* Store supplier details:

  * Name
  * Contact information
  * Address
* Track procurement:

  * Product purchased
  * Quantity
  * Cost per unit
  * Total cost
  * Payment type:

    * Paid upfront
    * Credit
  * Payment status
* Support multiple suppliers for the same product
* Maintain purchase history per supplier

---

## 3.2 Product Management

* Create and manage products
* Store product details:

  * Product name
  * Category
  * Unit of measure (kg, liter, unit, etc.)
  * MRP (Maximum Retail Price)
* Track procurement details:

  * Supplier-wise cost
  * Purchase batches
* Maintain:

  * Cost history
  * Supplier mapping
* Enable/disable products

---

## 3.3 Inventory Management

* Track stock levels in real-time:

  * Total stock available
  * Reserved stock (ordered but not delivered)
  * Available stock
* Maintain inventory per batch:

  * Batch ID
  * Supplier reference
  * Cost per batch
* Support:

  * Stock in (procurement)
  * Stock out (sales/delivery)
* Maintain stock movement logs:

  * Date/time
  * Source/destination
  * Quantity
* Low stock alerts

---

## 3.4 Customer Management

* Add, update, enable/disable customers
* Store customer details:

  * Business name
  * Contact person
  * Phone/email
  * Location/address
  * Client type/category
* Integrated with accounting:

  * Ledger view
  * Outstanding balance
  * Advance balance
* Track:

  * Credit behavior
  * Payment history

---

## 3.5 Pricing Management (Customer-Specific Pricing)

* Maintain price list per customer:

  * Product
  * Agreed price
* Support different prices per customer
* Track price changes over time
* Apply pricing automatically during order creation

---

## 3.6 Order Management

### Order Creation

* Staff creates orders on behalf of customers
* Select:

  * Customer
  * Products
  * Quantities
* System auto-applies customer-specific pricing

### Order Lifecycle

* Order statuses:

  * Created
  * Confirmed
  * Ready for delivery
  * Out for delivery
  * Delivered
* Track timestamps for each stage

### Delivery Management

* Assign orders to staff
* Mark delivery status
* Capture delivery confirmation

### Financial Impact

* Order contributes to:

  * Invoice generation
  * Customer ledger
  * Inventory deduction

---

## 3.7 Accounting System (Integrated with Customer Management)

### Overview

* Centralized accounting system tightly integrated with:

  * Customer management
  * Order management
  * Payment tracking
* Maintains real-time financial position of each customer

---

### Core Principles

* Every transaction is linked to:

  * Customer
  * Invoice or order
* Maintain running balance per customer:

  * Debit (customer owes business)
  * Credit (customer advance/payment)
* Accounting data is automatically generated from:

  * Orders
  * Invoices
  * Payments

---

### Customer Ledger (Account View)

* Each customer has a dedicated ledger
* Chronological transaction history

#### Ledger Entries Include:

* Invoice generated
* Order delivered
* Payment received
* Adjustments

#### Fields per Entry:

* Date
* Transaction type (Invoice / Payment / Adjustment)
* Reference ID (Order/Invoice)
* Debit amount
* Credit amount
* Running balance

---

### Invoice Management

#### Invoice Generation

* Generate invoice:

  * On delivery
  * On demand (manual trigger)
* Invoice includes:

  * Customer details
  * List of products:

    * Quantity
    * Price
    * Total per item
  * Total invoice value
  * Date range (e.g., last invoice to current)
  * Invoice date
  * Due date

#### Invoice Features

* Unique invoice ID
* Ability to:

  * Send/share invoice (PDF or digital)
* Filter invoices by:

  * Date range
  * Customer
* Track:

  * Paid invoices
  * Unpaid invoices
  * Partially paid invoices

---

### Receipt Management (Merged with Payment System)

#### Receipt Generation

* Generate receipt when payment is recorded
* Receipt linked to:

  * Customer
  * Invoice(s)

#### Receipt Includes:

* Payment date
* Amount received
* Payment mode:

  * Cash
  * Bank transfer
  * Digital
* Linked invoices (if applicable)
* Remaining balance

---

### Combined Statement (Invoice + Payment View)

* Generate unified statement per customer
* Shows:

  * Invoices issued
  * Payments received
  * Outstanding balance

#### Features

* Filter by:

  * Date range (e.g., last invoice to present)
  * Custom date selection
* Includes:

  * Itemized order details
  * Dates of transactions
  * Running balance
* Can act as:

  * Payment request document
  * Account summary

---

### Payment Tracking

* Record payments:

  * Date
  * Amount
  * Mode
* Link payments to:

  * Specific invoices (optional)
  * Customer account (general)
* Support:

  * Partial payments
  * Advance payments
* Automatically update:

  * Customer ledger
  * Outstanding balance

---

## 3.8 Reporting

### Time-Based Reports

* Monthly
* Quarterly
* Annual

### Inventory Reports

* Stock levels
* Stock movement
* Low stock alerts

### Sales Reports

* Product-wise sales
* Customer-wise sales

### Financial Reports

* Outstanding balances
* Payment collections
* Revenue summary

---

## 3.9 Order Aging Reports

* Track unpaid invoices per customer
* Categorize:

  * 0–30 days
  * 31–60 days
  * 61–90 days
  * 90+ days
* Highlight overdue accounts

---

## 3.10 Analytics

### Product Analytics

* Sales volume per product
* Profit margin:

  * Selling price vs cost
* Fast vs slow moving products

### Customer Analytics

* Revenue per customer
* Profitability per customer
* Purchase frequency

### Pricing Analytics

* Margin comparison across customers
* Effect of custom pricing

---
