---

# Roles and Permissions

## Distribution Chain Streamlining System

---

## Overview

* The system follows a **role-based access control model**
* Two primary roles:

  * Staff (Better name to be decided later)
  * Admin
* Admin has full control over all system operations
* Staff has limited, operational-level access

---

## 1. Staff Role

### Purpose

* Handle day-to-day field operations
* Interact with customers
* Manage orders and basic customer data

---

### Capabilities

#### Customer Management

* Create new customers
* Update customer information:

  * Name
  * Contact details
  * Location
  * Business type

---

#### Pricing Management

* Create and update **customer-specific price lists**
* Assign:
  * Product
  * Price to a specific customer

---

#### Order Management

* Create orders on behalf of customers
* Add:

  * Products
  * Quantities
* Automatically apply customer pricing
* Update order status:

  * Created
  * Confirmed
  * Ready for delivery
  * Delivered

---

#### Inventory Access

* View inventory (read-only)

  * Available stock
  * Product availability
* Cannot:

  * Modify stock
  * Adjust inventory

---

#### Restrictions

* Cannot access:

  * Full accounting system
  * Supplier data
  * Financial reports
* Cannot:

  * Record payments
  * Modify ledger entries
  * Perform stock adjustments

---

## 2. Admin Role

### Purpose

* Full system control
* Manage operations, finances, inventory, and users

---

### Capabilities

#### Includes All Staff Permissions

* Admin can perform all actions available to Staff

---

### Supplier Management

* Create and manage suppliers
* View supplier details and history
* Access supplier ledger:

  * Purchases
  * Payments made
  * Outstanding balances

---

### Procurement Management

* Record stock purchases from suppliers
* Define:

  * Product
  * Quantity
  * Cost
  * Supplier
* Handle:

  * Upfront payments
  * Credit purchases

---

### Supplier Payments

* Record payments made to suppliers
* Track:

  * Payment date
  * Amount
  * Mode
* Update supplier ledger automatically

---

### Inventory Management

* Full control over inventory
* Perform:

  * Stock additions (procurement)
  * Stock adjustments:

    * Damaged goods
    * Expired items
    * Manual corrections
* Maintain accurate stock levels

---

### Product Management

* Create and update product information:

  * Name
  * Category
  * Unit of measure
  * MRP
* Enable/disable products

---

### Customer Accounting & Ledger

* View full customer ledger
* Monitor:

  * Outstanding balances
  * Payment history
* Make manual accounting entries (if needed)

---

### Payment Handling (Customer Side)

* Record customer payments
* Update:

  * Ledger
  * Outstanding balance
* Handle:

  * Partial payments
  * Advance payments
  * Full settlements

---

### Invoice and Statement Management

* Generate and print:

  * Invoices
  * Receipts
  * Customer statements
* Share documents with customers
* Generate statements for:

  * Specific date ranges
  * Monthly summaries

---

### Reporting and Analytics

* Access all reports:

  * Financial reports
  * Sales reports
  * Inventory reports
* View analytics:

  * Product performance
  * Customer profitability

---

### Staff Management

* Create staff accounts
* Update staff information
* Disable staff accounts
* No deletion of staff accounts (for audit/history integrity)

---

## 3. Key Design Principles

* Clear separation between:

  * Operational role (Staff)
  * Control role (Admin)
* Financial actions are restricted to Admin
* Inventory integrity is protected by limiting modification access
* All critical actions are traceable for accountability

---
