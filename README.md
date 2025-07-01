# 🛍️ E-Commerce Product Catalog Database

This project provides a robust and scalable **relational database schema** for managing an **e-commerce product catalog**. It is designed to support a wide variety of product configurations, variations, attributes, and inventory management functionalities.

---

## 📚 Overview

The database is structured to accommodate the following:

* Brand and Category management
* Product listing with multiple images
* Item-level stock and pricing
* Support for color, size, and custom product variations
* Flexible attribute assignment with typed values

---

## 🗂️ Database Schema

### 🏷️ `brand`

Stores brand information.

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
name VARCHAR(100) NOT NULL
```

### 📂 `product_category`

Organizes products into categories.

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
name VARCHAR(100) NOT NULL  
description TEXT
```

### 📦 `product`

Main product listing, linked to brand and category.

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
name VARCHAR(150) NOT NULL  
brand_id INT  
category_id INT  
base_price DECIMAL(10, 2) NOT NULL
```

### 🖼️ `product_image`

Stores image URLs related to products.

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
product_id INT NOT NULL  
image_url VARCHAR(255) NOT NULL
```

### 🧾 `product_item`

Represents purchasable units of a product with stock info.

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
product_id INT NOT NULL  
price DECIMAL(10, 2)  
stock_quantity INT DEFAULT 0
```

### 🎨 `color`

Color options available for product variations.

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
name VARCHAR(50)  
hex_code CHAR(7)
```

### 📏 `size_category`

Defines size categories (e.g., Clothing Size, Shoe Size).

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
name VARCHAR(100)
```

### 📐 `size_option`

Specific size options within a size category.

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
size_category_id INT  
label VARCHAR(10)  
value VARCHAR(20)
```

### 🔄 `product_variation`

Links a product item to specific color and size.

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
product_item_id INT NOT NULL  
color_id INT  
size_option_id INT
```

### 🧩 `attribute_category`

Categorizes custom product attributes.

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
name VARCHAR(100)
```

### 🧬 `attribute_type`

Specifies the data type for attributes (text, number, boolean).

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
name VARCHAR(100)  
data_type ENUM('text', 'number', 'boolean') NOT NULL
```

### 🏷️ `product_attribute`

Stores specific attribute values for a product.

```sql
id INT PRIMARY KEY AUTO_INCREMENT  
product_id INT NOT NULL  
attribute_category_id INT  
attribute_type_id INT  
value VARCHAR(255)
```

---

## ⚙️ Use Cases

* 🛒 E-commerce platforms
* 🧑‍💻 Inventory systems
* 🧱 Product data modeling
* 📦 Warehouse management integrations

---

## 🧪 How to Use

1. Clone the repository or copy the SQL script.
2. Run the script in your MySQL-compatible database (e.g., MySQL, MariaDB).
3. Start inserting brand, product, and variation data for your application.

---



