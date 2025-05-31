# Laravel Inventory Management

## Overview

Simple Laravel inventory system to manage products with add, edit, delete, search, and now export features.

---

## Features

* Add new products (name, buying price, selling price, quantity)
* Edit existing products via modal popup
* Delete products
* Search products live on the frontend
* Database seeding with dummy products (optional)
* **Export products to Excel (.xlsx)**
* **Export products to PDF**

---

## Installation

1. **Clone repo**

   ```bash
   git clone your-repo-url
   cd your-project-folder
   ```

2. **Install dependencies**

   ```bash
   composer install
   ```

3. **Configure environment**
   Copy `.env.example` to `.env` and update database credentials.

4. **Generate app key**

   ```bash
   php artisan key:generate
   ```

5. **Run migrations and seed database**

   ```bash
   php artisan migrate --seed
   ```

6. **Install export packages**

   ```bash
   composer require maatwebsite/excel
   composer require barryvdh/laravel-dompdf
   ```

7. **Run local development server**

   ```bash
   php artisan serve
   ```

---

## Database

* `products` table stores:

  * `id`
  * `name`
  * `buying_price`
  * `selling_price`
  * `quantity`
  * `timestamps`

* Seeder populates dummy data using Laravel factories.

---

## Code Highlights

* **Model:** `app/Models/Product.php`
  Uses `HasFactory` trait for seeding.

* **Controller:** `app/Http/Controllers/ProductController.php`
  Contains CRUD logic plus new export methods for Excel and PDF.

* **Routes:** `routes/web.php`
  Defined routes for product CRUD operations and exports.

* **Views:**

  * Main Blade template with product form, table, search, and modal edit.
  * New Blade for PDF export layout (`products/pdf.blade.php`).

---

## Export Features

* **Excel export:** Uses `maatwebsite/excel` package with `ProductsExport` class to export all products to `.xlsx` file.

* **PDF export:** Uses `barryvdh/laravel-dompdf` to generate PDF from a Blade view of all products.

* Export buttons added in the main view for user access.

---

## Usage

* Visit `/` to see the product list.
* Use the form to add new products.
* Click "Edit" button to open modal for editing product details.
* Use the search box to filter products by name or details.
* Click "Delete" to remove products.
* Click **Export Excel** to download an Excel file of all products.
* Click **Export PDF** to download a PDF document of all products.

---

## Notes

* Ensure `Product` model uses the `HasFactory` trait for seeding.
* Export packages must be installed via composer.
* Customize CSS in `public/css/style.css` or inline for improved UI.
* For production, implement authentication and user-specific inventories as needed.

---
