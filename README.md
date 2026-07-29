# POS Modern Desktop Point of Sale System

> A modern offline desktop Point of Sale (POS) system built for service businesses. Designed to simplify sales, inventory management, FIFO stock tracking, customer credit management, reporting, and data backup—all in a fast and intuitive desktop application.

![Offline](https://img.shields.io/badge/Offline-100%25-success)


##  🟡About

Honda POS is a fully offline desktop Point of Sale application developed using **React, TypeScript, Electron, and Tailwind CSS**.

The application provides an all-in-one solution for retail stores by combining:

- Billing & Checkout
- Inventory Management
- FIFO Batch Tracking
- Customer Credit (Udhar)
- Reports & Analytics
- Backup & Restore
- Receipt Printing

#  🛒 Core POS Features


## 1) Point of Sale (POS) — Billing & Checkout

- Real-time product search
- Barcode Scanner Support
- 6-column product grid
- Editable quantity & price

### Batch-Aware Pricing
- Oldest-batch price display
- Automatic fallback
- Cart consistency

### Payment & Checkout
- Full payment 
- Partial payment with customer credit
- Zero amount entry (full credit)
- Optional customer linking
- Auto stock deduction

### Receipt Generation
- Invoice design
- Item table
- Discount display
- Custom labels
- Bold credit label option
- Terms & Conditions
- Print button

![Description of the image](demo/1.jpg)

![Description of the image](demo/11.jpg)



## 2) Products Management
### Product CRUD & Organization
- Add new products
- Image upload
- Edit products
- Delete products
- Drag-and-drop reordering
- Category management
- Stock display
 #### Search & Filtering
- Real-time search
- Category filter
- Profit calculation
- Barcode input field

![Description of the image](demo/2.jpg)




## 3) Inventory Management

- Live Stock Tracking
- Low Stock Alerts
- Restocking
- Warehouse Capacity Indicators
- Stock Reports


![Description of the image](demo/3.jpg)



## 4) Customer Management

- Customer Profiles
- Purchase History
- Pending Credit (Udhar)
- Manual Payments
- Manual Dues
- Customer Statements
- Favorite Customers

![Description of the image](demo/4.jpg)


## 5) Reports & Analytics

- Daily Reports
- Weekly Reports
- Monthly Reports
- Revenue Analytics
- Top Selling Products
- Revenue by Category
- Transaction History
- Export CSV

![Description of the image](demo/5.jpg)

![Description of the image](demo/6.jpg)




## 6) Expenses Page
- Add Expenses 
- Categorize 
- Date Tracking 
- Monthly View 
- Category Breakdown
- Search & Filter 
- Edit & Delete 
- Expense Reports 
![Description of the image](demo/7.jpg)



## 7) FIFO Batch Tracking

One of the major features of this application.

- Multiple purchase batches

- Batch-wise Cost Price

- Batch-wise Selling Price

- Oldest Batch First (FIFO)

- Accurate Profit Calculation

- Batch Consumption Logs


![Description of the image](demo/8.jpg)

## 8) Settings

- Shop Information
- Receipt Customization
- Font Customization
- Thermal Printer Support
- Backup & Restore
- Export to Excel
- Low Stock Configuration


![Description of the image](demo/9.jpg)

![Description of the image](demo/10.jpg)

## 🟡System Architecture & Data Flow
```
Electron Desktop Shell (Windows 10/11)
├── React 19 + TypeScript UI Layer
│   ├── POS Page
│   ├── Products Page
│   ├── Batches Page (FIFO)
│   ├── Inventory Page
│   ├── Customers Page
│   ├── Reports Page
│   └── Settings Page (Backup/Restore)
│
├── Store Modules (Data Layer)
│   ├── store/db.ts
│   │   └── CRUD: products, sales, customers, payments, settings
│   └── store/batch-fifo.ts
│       └── FIFO logic: addProductBatch, consumeProductBatches, calculateProfitFIFO
│
└── Browser localStorage (Persistence)
    ├── pharma_products
    ├── pharma_categories
    ├── pharma_units
    ├── pharma_sales
    ├── pharma_customers
    ├── pharma_payments
    ├── pharma_batches ★ (NEW)
    ├── pharma_batch_consumptions ★ (NEW)
    └── pharma_settings
```

## 🟡Sale Transaction Pipeline
```
Scan / Search Product
        ↓
    Add to Cart
        ↓
Checkout: Payment or Link Customer
        ↓
consumeProductBatches() — FIFO
        ↓
Save Sale + Receipt
        ↓
If customer linked & amount paid < total:
  → Remaining balance added to customer's pending udhar
```
