---

# Database Schema

## Distribution Chain Streamlining System

---

## Design Principles

* Ledger-based accounting (no balance stored, always computed or cached safely)
* Separation of:

  * Operational tables (orders, inventory)
  * Financial tables (invoices, payments, ledger)
* Support for:

  * Batch-level inventory tracking
  * Customer-specific pricing
* All critical entities are auditable (timestamps, references)

---

# 1. Core Entities

---

## 1.1 Users

```sql
users (
  id UUID PK,
  name VARCHAR,
  email VARCHAR UNIQUE,
  phone VARCHAR,
  role ENUM('admin', 'staff'),
  is_active BOOLEAN,
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)
```

---

## 1.2 Customers

```sql
customers (
  id UUID PK,
  name VARCHAR,
  contact_person VARCHAR,
  phone VARCHAR,
  email VARCHAR,
  address TEXT,
  client_type VARCHAR,
  is_active BOOLEAN,
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)
```

---

## 1.3 Suppliers

```sql
suppliers (
  id UUID PK,
  name VARCHAR,
  phone VARCHAR,
  email VARCHAR,
  address TEXT,
  is_active BOOLEAN,
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)
```

---

## 1.4 Products

```sql
products (
  id UUID PK,
  name VARCHAR,
  category VARCHAR,
  unit VARCHAR, -- kg, liter, unit
  mrp DECIMAL,
  is_active BOOLEAN,
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)
```

---

# 2. Pricing

---

## 2.1 Customer Price List

```sql
customer_prices (
  id UUID PK,
  customer_id UUID FK -> customers.id,
  product_id UUID FK -> products.id,
  price DECIMAL,
  created_at TIMESTAMP,
  updated_at TIMESTAMP,
  UNIQUE(customer_id, product_id)
)
```

---

# 3. Procurement & Inventory

---

## 3.1 Purchase Orders (Procurement)

```sql
purchase_orders (
  id UUID PK,
  supplier_id UUID FK -> suppliers.id,
  total_amount DECIMAL,
  payment_type ENUM('cash', 'credit'),
  status ENUM('created', 'received'),
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)
```

---

## 3.2 Purchase Items

```sql
purchase_items (
  id UUID PK,
  purchase_order_id UUID FK -> purchase_orders.id,
  product_id UUID FK -> products.id,
  quantity DECIMAL,
  cost_price DECIMAL,
  total_cost DECIMAL
)
```

---

## 3.3 Inventory Batches

```sql
inventory_batches (
  id UUID PK,
  product_id UUID FK -> products.id,
  supplier_id UUID FK -> suppliers.id,
  purchase_item_id UUID FK -> purchase_items.id,
  quantity_initial DECIMAL,
  quantity_remaining DECIMAL,
  cost_price DECIMAL,
  created_at TIMESTAMP
)
```

---

## 3.4 Inventory Movements

```sql
inventory_movements (
  id UUID PK,
  product_id UUID FK -> products.id,
  batch_id UUID FK -> inventory_batches.id,
  type ENUM('in', 'out', 'adjustment'),
  quantity DECIMAL,
  reference_type VARCHAR, -- order, purchase, adjustment
  reference_id UUID,
  created_at TIMESTAMP
)
```

---

# 4. Orders

---

## 4.1 Orders

```sql
orders (
  id UUID PK,
  customer_id UUID FK -> customers.id,
  created_by UUID FK -> users.id,
  status ENUM('created', 'confirmed', 'ready', 'out_for_delivery', 'delivered'),
  total_amount DECIMAL,
  created_at TIMESTAMP,
  updated_at TIMESTAMP
)
```

---

## 4.2 Order Items

```sql
order_items (
  id UUID PK,
  order_id UUID FK -> orders.id,
  product_id UUID FK -> products.id,
  quantity DECIMAL,
  price DECIMAL,
  total_price DECIMAL
)
```

---

# 5. Accounting System

---

## 5.1 Invoices

```sql
invoices (
  id UUID PK,
  customer_id UUID FK -> customers.id,
  invoice_number VARCHAR UNIQUE,
  total_amount DECIMAL,
  issue_date DATE,
  due_date DATE,
  status ENUM('unpaid', 'partial', 'paid'),
  created_at TIMESTAMP
)
```

---

## 5.2 Invoice Items

```sql
invoice_items (
  id UUID PK,
  invoice_id UUID FK -> invoices.id,
  product_id UUID FK -> products.id,
  quantity DECIMAL,
  price DECIMAL,
  total DECIMAL
)
```

---

## 5.3 Payments (Customer Payments)

```sql
payments (
  id UUID PK,
  customer_id UUID FK -> customers.id,
  amount DECIMAL,
  payment_mode ENUM('cash', 'bank', 'digital'),
  payment_date DATE,
  reference_note VARCHAR,
  created_at TIMESTAMP
)
```

---

## 5.4 Payment Allocation (Important)

```sql
payment_allocations (
  id UUID PK,
  payment_id UUID FK -> payments.id,
  invoice_id UUID FK -> invoices.id,
  amount DECIMAL
)
```

---

# 6. Ledger System (Core Accounting)

---

## 6.1 Customer Ledger

```sql
customer_ledger (
  id UUID PK,
  customer_id UUID FK -> customers.id,
  transaction_type ENUM('invoice', 'payment', 'adjustment'),
  reference_id UUID,
  reference_type VARCHAR,
  debit DECIMAL DEFAULT 0,
  credit DECIMAL DEFAULT 0,
  created_at TIMESTAMP
)
```

---

## 6.2 Supplier Ledger

```sql
supplier_ledger (
  id UUID PK,
  supplier_id UUID FK -> suppliers.id,
  transaction_type ENUM('purchase', 'payment'),
  reference_id UUID,
  debit DECIMAL DEFAULT 0,  -- you owe supplier
  credit DECIMAL DEFAULT 0, -- you paid supplier
  created_at TIMESTAMP
)
```

---

# 7. Mapping Tables to User Stories

---

## Supplier & Product Setup

* suppliers
* products

---

## Procurement

* purchase_orders
* purchase_items
* inventory_batches
* inventory_movements
* supplier_ledger

---

## Inventory Tracking

* inventory_batches
* inventory_movements

---

## Customer & Pricing

* customers
* customer_prices

---

## Order Flow

* orders
* order_items

---

## Delivery → Accounting Trigger

* orders (status = delivered)
* invoices
* invoice_items
* customer_ledger

---

## Payments & Receipts

* payments
* payment_allocations
* customer_ledger

---

## Statements & Ledger

* customer_ledger
* invoices
* payments

---

## Supplier Settlement

* supplier_ledger
* payments 

---

# 8. Important Notes

---

## Ledger Rules

* Invoice:

  * Debit customer ledger
* Payment:

  * Credit customer ledger

---

## Balance Calculation

```sql
balance = SUM(debit) - SUM(credit)
```

---

## Inventory Deduction Strategy

* FIFO (recommended):

  * Deduct from oldest batch first

---

## Data Integrity

* Never delete:

  * invoices
  * payments
  * ledger entries
* Use:

  * soft delete or status flags

---
