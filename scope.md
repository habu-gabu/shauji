---

# Distribution Chain Streamlining System

## Software Requirements Document (SRD)

---

## 1. Introduction

### 1.1 Purpose

* Define requirements for a distribution chain and inventory management system
* Streamline procurement, inventory tracking, sales, and reporting
* Provide visibility into stock, costs, pricing, and customer transactions

### 1.2 Scope

* Covers end-to-end operations:

  * Supplier procurement
  * Inventory management
  * Product tracking
  * Customer management
  * Order processing
  * Pricing management
  * Reporting and analytics
* Multi-user system with role-based access (admin and staff)

---

## 2. User Roles

### 2.1 Admin

* Full system access
* Manage products, suppliers, customers, pricing
* View analytics and reports
* Overall monitoring privilege

### 2.2 Staff (Proper name to be decided)

* Place orders on behalf of customers
* Update order status
* View assigned customers and pricing
* Limited access to inventory and product data

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
* Maintain product-level metadata:

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

  * Purchase batch tracking
  * Cost per batch
* Support:

  * Stock in (procurement)
  * Stock out (sales/delivery)
* Alerts:

  * Low stock alerts
* Stock movement logs:

  * Date/time
  * Source (supplier/customer)
  * Quantity change

---

## 3.4 Customer Management

* Add, update, enable/disable customers
* Store customer details:

  * Business name
  * Contact person
  * Phone/email
  * Location/address
  * Client type/category
* Customer account view:

  * Order history
  * Payment history
  * Outstanding balance
  * Advance payments
* Track:

  * Credit limit (optional)
  * Payment behavior

---

## 3.5 Pricing Management (Customer-Specific Pricing)

* Maintain price list per customer:

  * Product
  * Agreed price
* Support:

  * Different prices for different customers
* Track price changes over time
* Apply pricing automatically during order creation

---

## 3.6 Order Management

### Order Creation

* Staff can create orders on behalf of customers
* Select:

  * Customer
  * Products
  * Quantities
* Auto-fetch customer-specific pricing

### Order Lifecycle

* Order statuses:

  * Created
  * Confirmed
  * Ready for delivery
  * Out for delivery
  * Delivered
* Track timestamps for:

  * Order creation
  * Status changes
  * Delivery completion

### Delivery Management

* Assign orders to staff
* Mark delivery status
* Capture delivery confirmation

### Financial Tracking

* Order value calculation
* Payment type:

  * Cash
  * Credit
  * Digital
* Update customer balance

---

## 3.7 Payment Management

* Record payments from customers:

  * Date
  * Amount
  * Mode (cash, bank, digital)
* Link payments to:

  * Orders (optional)
  * Customer account
* Track:

  * Outstanding balance
  * Advance payments
* Payment history logs

---

## 3.8 Reporting

### Standard Reports

* Monthly reports
* Quarterly reports
* Annual reports

### Inventory Reports

* Current stock report
* Stock movement report
* Low stock report

### Sales Reports

* Product-wise sales
* Customer-wise sales
* Revenue reports

### Financial Reports

* Profit/loss estimation
* Outstanding payments
* Cash flow summaries

---

## 3.9 Order Aging Reports

* Track pending payments per customer
* Categorize aging:

  * 0–30 days
  * 31–60 days
  * 61–90 days
  * 90+ days
* Customer-wise aging summary
* Highlight overdue accounts

---

## 3.10 Analytics

### Product Analytics

* Sales volume per product
* Profit margin per product:

  * Selling price vs cost
* Fast-moving vs slow-moving products

### Customer Analytics

* Revenue per customer
* Profitability per customer
* Purchase frequency

### Pricing Analytics

* Impact of different pricing per customer
* Margin comparison across customers

---

## 4. Non-Functional Requirements

### Performance

* Handle concurrent users (admin + multiple staff)
* Fast response for order creation and inventory updates

### Scalability

* Support increasing number of:

  * Products
  * Customers
  * Orders

### Security

* Role-based access control
* Secure authentication
* Data protection

### Usability

* Simple UI for field staff
* Dashboard for admin insights

### Reliability

* Data consistency across modules
* Backup and recovery support

---

## 5. System Architecture (High-Level)

* Frontend:

  * Web or mobile interface for admin and staff
* Backend:

  * REST API or similar service
* Database:

  * Relational database for structured data
* Modules:

  * Inventory Service
  * Order Service
  * Customer Service
  * Reporting Service

---
