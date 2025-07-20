# food_ordering_app
# Food Ordering App - Complete Feature Specification

## 🎯 Core Features Overview

### 1. User Authentication & Management (P1)
**Purpose**: จัดการผู้ใช้งานทั้งหมดในระบบ

**Input Parameters**:
- Registration: email, password, first_name, last_name, phone, address
- Login: email/phone, password
- Profile Update: user_id, updated_fields

**Output Parameters**:
- JWT token, user_profile, authentication_status
- Error messages for invalid credentials

**Capabilities**:
- สมัครสมาชิกและยืนยันอีเมล
- เข้าสู่ระบบด้วย email/phone
- จัดการโปรไฟล์ส่วนตัว
- รีเซ็ตรหัสผ่าน
- จัดการที่อยู่จัดส่งหลายที่

### 2. Menu & Food Management (P2)
**Purpose**: จัดการเมนูอาหารและข้อมูลสินค้า

**Input Parameters**:
- Add Item: name, description, price, category_id, ingredients[], image_url, preparation_time
- Update Item: item_id, updated_fields
- Search: keywords, category_filter, price_range

**Output Parameters**:
- Menu items list, item_details, categories, search_results

**Capabilities**:
- เพิ่ม/แก้ไข/ลบรายการอาหาร
- จัดหมวดหมู่อาหาร
- อัพโหลดรูปภาพสินค้า
- กำหนดราคาและเวลาเตรียมอาหาร
- ค้นหาและกรองเมนู
- จัดการส่วนผสมของแต่ละเมนู

### 3. Order Processing (P3)
**Purpose**: จัดการกระบวนการสั่งอาหารทั้งหมด

**Input Parameters**:
- Create Order: user_id, items[], delivery_address, payment_method, special_instructions
- Update Status: order_id, new_status
- Cancel Order: order_id, reason

**Output Parameters**:
- order_id, order_details, total_amount, estimated_delivery_time

**Capabilities**:
- สร้างออเดอร์ใหม่
- คำนวณราคารวมและค่าส่ง
- จัดการสถานะออเดอร์ (pending, confirmed, preparing, ready, delivered, cancelled)
- ตรวจสอบความพร้อมของส่วนผสม
- กำหนดเวลาจัดส่ง
- ยกเลิกออเดอร์

### 4. Payment Processing (P4)
**Purpose**: จัดการการชำระเงินทุกรูปแบบ

**Input Parameters**:
- Process Payment: order_id, payment_method, amount, card_details/qr_code
- Refund: payment_id, refund_amount, reason

**Output Parameters**:
- payment_status, transaction_id, receipt_data

**Capabilities**:
- รับชำระเงินหลายช่องทาง (บัตรเครดิต, QR Code, เงินสด)
- ตรวจสอบและยืนยันการชำระเงิน
- คืนเงินเมื่อยกเลิกออเดอร์
- สร้างใบเสร็จอิเล็กทรอนิกส์
- จัดการการผ่อนชำระ

### 5. Inventory Management (P5)
**Purpose**: จัดการสต็อกส่วนผสมและวัตถุดิบ

**Input Parameters**:
- Update Stock: ingredient_id, quantity_change, operation_type
- Set Alert Level: ingredient_id, minimum_quantity
- Manual Count: ingredient_id, actual_quantity

**Output Parameters**:
- current_stock_levels, low_stock_alerts, inventory_reports

**Capabilities**:
- ติดตามสต็อกแบบ real-time
- แจ้งเตือนเมื่อสต็อกเหลือน้อย
- อัพเดทสต็อกอัตโนมัติเมื่อมีออเดอร์
- จัดการวันหมดอายุของวัตถุดิบ
- คำนวณต้นทุนวัตถุดิบ

### 6. Supplier Management (P6)
**Purpose**: จัดการผู้จำหน่ายและการสั่งซื้อวัตถุดิบ

**Input Parameters**:
- Create Purchase Order: supplier_id, items[], delivery_date, budget_limit
- Update Supplier: supplier_id, contact_info, terms

**Output Parameters**:
- purchase_order_id, supplier_list, delivery_schedule

**Capabilities**:
- จัดการข้อมูลผู้จำหน่าย
- สร้างใบสั่งซื้ออัตโนมัติ
- ติดตามการจัดส่งวัตถุดิบ
- เปรียบเทียบราคาจากหลายผู้จำหน่าย
- ประเมินประสิทธิภาพผู้จำหน่าย

### 7. Kitchen Operations (P7)
**Purpose**: จัดการการทำอาหารและคิวการผลิต

**Input Parameters**:
- Add to Queue: order_id, priority_level, estimated_prep_time
- Update Cooking Status: order_id, status, chef_id

**Output Parameters**:
- cooking_queue, preparation_status, completion_time

**Capabilities**:
- จัดคิวการทำอาหารตามลำดับความสำคัญ
- ติดตามสถานะการเตรียมอาหาร
- กำหนดเชฟที่รับผิดชอบแต่ละเมนู
- คำนวณเวลาเตรียมอาหารรวม
- แจ้งเตือนเมื่ออาหารเสร็จ

### 8. Delivery Management (P8)
**Purpose**: จัดการการจัดส่งอาหาร

**Input Parameters**:
- Assign Delivery: order_id, delivery_person_id, route_optimization
- Track Delivery: delivery_id, current_location, status

**Output Parameters**:
- delivery_assignment, tracking_info, estimated_arrival

**Capabilities**:
- มอบหมายงานจัดส่งให้คนส่งของ
- ติดตามตำแหน่งการจัดส่งแบบ real-time
- คำนวณเส้นทางที่เหมาะสม
- แจ้งเตือนลูกค้าเมื่อใกล้ถึง
- จัดการปัญหาการจัดส่ง

### 9. Notification System (P9)
**Purpose**: จัดการการแจ้งเตือนทุกประเภท

**Input Parameters**:
- Send Notification: user_id, message, notification_type, channel
- Schedule Notification: send_time, recipients[], content

**Output Parameters**:
- delivery_status, notification_history

**Capabilities**:
- ส่งการแจ้งเตือนผ่านหลายช่องทาง (Push, SMS, Email)
- แจ้งเตือนสถานะออเดอร์
- โปรโมชันและข้อเสนอพิเศษ
- แจ้งเตือนระบบสำหรับแอดมิน
- กำหนดเวลาส่งข้อความล่วงหน้า

### 10. Analytics & Reporting (P10)
**Purpose**: สร้างรายงานและวิเคราะห์ข้อมูล

**Input Parameters**:
- Generate Report: report_type, date_range, filters[], format
- Get Analytics: metric_type, granularity, comparison_period

**Output Parameters**:
- reports[], charts[], kpi_metrics, insights

**Capabilities**:
- รายงานยอดขาย และรายได้
- วิเคราะห์พฤติกรรมลูกค้า
- ประสิทธิภาพการดำเนินงาน
- รายงานสต็อกและต้นทุน
- การพยากรณ์ยอดขาย

## 🗃️ Database Schema & Attributes

### Users Table
```sql
user_id (PK): BIGINT AUTO_INCREMENT
email: VARCHAR(255) UNIQUE NOT NULL
phone: VARCHAR(20) UNIQUE
password_hash: VARCHAR(255) NOT NULL
first_name: VARCHAR(100) NOT NULL
last_name: VARCHAR(100) NOT NULL
profile_image: VARCHAR(500)
date_of_birth: DATE
gender: ENUM('M', 'F', 'Other')
user_type: ENUM('customer', 'admin', 'chef', 'delivery') DEFAULT 'customer'
is_email_verified: BOOLEAN DEFAULT FALSE
is_phone_verified: BOOLEAN DEFAULT FALSE
loyalty_points: INT DEFAULT 0
total_orders: INT DEFAULT 0
total_spent: DECIMAL(10,2) DEFAULT 0.00
last_login_at: TIMESTAMP
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
is_active: BOOLEAN DEFAULT TRUE
```

### User_Addresses Table
```sql
address_id (PK): BIGINT AUTO_INCREMENT
user_id (FK): BIGINT NOT NULL
address_type: ENUM('home', 'office', 'other') DEFAULT 'home'
address_line1: VARCHAR(255) NOT NULL
address_line2: VARCHAR(255)
city: VARCHAR(100) NOT NULL
district: VARCHAR(100) NOT NULL
province: VARCHAR(100) NOT NULL
postal_code: VARCHAR(10) NOT NULL
country: VARCHAR(100) DEFAULT 'Thailand'
latitude: DECIMAL(10, 8)
longitude: DECIMAL(11, 8)
delivery_instructions: TEXT
is_default: BOOLEAN DEFAULT FALSE
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Categories Table
```sql
category_id (PK): BIGINT AUTO_INCREMENT
name: VARCHAR(100) NOT NULL
name_th: VARCHAR(100)
description: TEXT
image_url: VARCHAR(500)
parent_category_id (FK): BIGINT (self-reference)
sort_order: INT DEFAULT 0
is_active: BOOLEAN DEFAULT TRUE
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Menu_Items Table
```sql
item_id (PK): BIGINT AUTO_INCREMENT
category_id (FK): BIGINT NOT NULL
name: VARCHAR(200) NOT NULL
name_th: VARCHAR(200)
description: TEXT
description_th: TEXT
price: DECIMAL(8,2) NOT NULL
cost: DECIMAL(8,2)
preparation_time: INT NOT NULL (minutes)
calories: INT
spice_level: ENUM('none', 'mild', 'medium', 'hot', 'very_hot') DEFAULT 'none'
is_vegetarian: BOOLEAN DEFAULT FALSE
is_vegan: BOOLEAN DEFAULT FALSE
is_gluten_free: BOOLEAN DEFAULT FALSE
allergens: JSON
nutritional_info: JSON
image_url: VARCHAR(500)
gallery_images: JSON
recipe_instructions: TEXT
serving_size: VARCHAR(50)
is_available: BOOLEAN DEFAULT TRUE
is_featured: BOOLEAN DEFAULT FALSE
popularity_score: INT DEFAULT 0
average_rating: DECIMAL(3,2) DEFAULT 0.00
total_reviews: INT DEFAULT 0
total_sold: INT DEFAULT 0
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Ingredients Table
```sql
ingredient_id (PK): BIGINT AUTO_INCREMENT
name: VARCHAR(200) NOT NULL
name_th: VARCHAR(200)
description: TEXT
unit_of_measure: VARCHAR(20) NOT NULL (kg, gram, liter, piece, etc.)
current_stock: DECIMAL(10,3) NOT NULL DEFAULT 0
minimum_stock: DECIMAL(10,3) NOT NULL DEFAULT 0
maximum_stock: DECIMAL(10,3) NOT NULL DEFAULT 1000
reorder_point: DECIMAL(10,3) NOT NULL DEFAULT 0
cost_per_unit: DECIMAL(8,2) NOT NULL
shelf_life_days: INT
storage_requirements: TEXT
supplier_id (FK): BIGINT
is_perishable: BOOLEAN DEFAULT FALSE
allergen_info: JSON
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Menu_Item_Ingredients Table
```sql
item_ingredient_id (PK): BIGINT AUTO_INCREMENT
item_id (FK): BIGINT NOT NULL
ingredient_id (FK): BIGINT NOT NULL
quantity_required: DECIMAL(10,3) NOT NULL
is_optional: BOOLEAN DEFAULT FALSE
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
UNIQUE KEY unique_item_ingredient (item_id, ingredient_id)
```

### Orders Table
```sql
order_id (PK): BIGINT AUTO_INCREMENT
user_id (FK): BIGINT NOT NULL
order_number: VARCHAR(50) UNIQUE NOT NULL
status: ENUM('pending', 'confirmed', 'preparing', 'ready', 'out_for_delivery', 'delivered', 'cancelled') DEFAULT 'pending'
order_type: ENUM('delivery', 'pickup', 'dine_in') DEFAULT 'delivery'
subtotal: DECIMAL(10,2) NOT NULL
tax_amount: DECIMAL(10,2) NOT NULL DEFAULT 0
delivery_fee: DECIMAL(10,2) NOT NULL DEFAULT 0
service_fee: DECIMAL(10,2) NOT NULL DEFAULT 0
discount_amount: DECIMAL(10,2) NOT NULL DEFAULT 0
total_amount: DECIMAL(10,2) NOT NULL
delivery_address_id (FK): BIGINT
estimated_delivery_time: TIMESTAMP
actual_delivery_time: TIMESTAMP
special_instructions: TEXT
payment_status: ENUM('pending', 'paid', 'failed', 'refunded') DEFAULT 'pending'
is_paid: BOOLEAN DEFAULT FALSE
chef_id (FK): BIGINT
delivery_person_id (FK): BIGINT
rating: INT (1-5)
review: TEXT
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Order_Items Table
```sql
order_item_id (PK): BIGINT AUTO_INCREMENT
order_id (FK): BIGINT NOT NULL
item_id (FK): BIGINT NOT NULL
quantity: INT NOT NULL DEFAULT 1
unit_price: DECIMAL(8,2) NOT NULL
total_price: DECIMAL(10,2) NOT NULL
special_instructions: TEXT
customizations: JSON
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
```

### Payments Table
```sql
payment_id (PK): BIGINT AUTO_INCREMENT
order_id (FK): BIGINT NOT NULL
payment_method: ENUM('cash', 'credit_card', 'debit_card', 'qr_code', 'bank_transfer', 'wallet') NOT NULL
amount: DECIMAL(10,2) NOT NULL
currency: VARCHAR(3) DEFAULT 'THB'
status: ENUM('pending', 'success', 'failed', 'cancelled', 'refunded') DEFAULT 'pending'
transaction_id: VARCHAR(255) UNIQUE
gateway_response: JSON
receipt_url: VARCHAR(500)
refund_amount: DECIMAL(10,2) DEFAULT 0.00
refund_reason: TEXT
processed_at: TIMESTAMP
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Suppliers Table
```sql
supplier_id (PK): BIGINT AUTO_INCREMENT
company_name: VARCHAR(255) NOT NULL
contact_person: VARCHAR(200)
phone: VARCHAR(20) NOT NULL
email: VARCHAR(255)
address: TEXT NOT NULL
tax_id: VARCHAR(50)
payment_terms: VARCHAR(100)
credit_limit: DECIMAL(12,2) DEFAULT 0
current_balance: DECIMAL(12,2) DEFAULT 0
rating: DECIMAL(3,2) DEFAULT 0
delivery_time_days: INT DEFAULT 1
is_active: BOOLEAN DEFAULT TRUE
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Purchase_Orders Table
```sql
purchase_order_id (PK): BIGINT AUTO_INCREMENT
supplier_id (FK): BIGINT NOT NULL
po_number: VARCHAR(50) UNIQUE NOT NULL
status: ENUM('draft', 'sent', 'confirmed', 'partially_received', 'received', 'cancelled') DEFAULT 'draft'
subtotal: DECIMAL(12,2) NOT NULL
tax_amount: DECIMAL(12,2) DEFAULT 0
total_amount: DECIMAL(12,2) NOT NULL
requested_delivery_date: DATE NOT NULL
actual_delivery_date: DATE
notes: TEXT
approved_by: BIGINT
approved_at: TIMESTAMP
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Purchase_Order_Items Table
```sql
po_item_id (PK): BIGINT AUTO_INCREMENT
purchase_order_id (FK): BIGINT NOT NULL
ingredient_id (FK): BIGINT NOT NULL
quantity_ordered: DECIMAL(10,3) NOT NULL
unit_price: DECIMAL(8,2) NOT NULL
total_price: DECIMAL(10,2) NOT NULL
quantity_received: DECIMAL(10,3) DEFAULT 0
expiry_date: DATE
batch_number: VARCHAR(100)
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
```

### Deliveries Table
```sql
delivery_id (PK): BIGINT AUTO_INCREMENT
order_id (FK): BIGINT NOT NULL
delivery_person_id (FK): BIGINT NOT NULL
assigned_at: TIMESTAMP NOT NULL
picked_up_at: TIMESTAMP
delivered_at: TIMESTAMP
status: ENUM('assigned', 'picked_up', 'in_transit', 'delivered', 'failed', 'cancelled') DEFAULT 'assigned'
current_location: POINT
estimated_arrival: TIMESTAMP
actual_arrival: TIMESTAMP
delivery_notes: TEXT
customer_rating: INT (1-5)
customer_feedback: TEXT
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Notifications Table
```sql
notification_id (PK): BIGINT AUTO_INCREMENT
user_id (FK): BIGINT NOT NULL
type: ENUM('order_status', 'promotion', 'system', 'delivery', 'payment') NOT NULL
title: VARCHAR(255) NOT NULL
message: TEXT NOT NULL
channel: ENUM('push', 'sms', 'email', 'in_app') DEFAULT 'in_app'
is_read: BOOLEAN DEFAULT FALSE
is_sent: BOOLEAN DEFAULT FALSE
scheduled_at: TIMESTAMP
sent_at: TIMESTAMP
metadata: JSON
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Reviews Table
```sql
review_id (PK): BIGINT AUTO_INCREMENT
order_id (FK): BIGINT NOT NULL
user_id (FK): BIGINT NOT NULL
item_id (FK): BIGINT
rating: INT NOT NULL (1-5)
title: VARCHAR(255)
comment: TEXT
images: JSON
is_verified_purchase: BOOLEAN DEFAULT TRUE
helpful_votes: INT DEFAULT 0
is_approved: BOOLEAN DEFAULT FALSE
response_from_restaurant: TEXT
responded_at: TIMESTAMP
created_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

## 🔗 Key Relationships & Foreign Keys

1. **Users** (1:N) **User_Addresses** - ผู้ใช้หนึ่งคนมีที่อยู่ได้หลายที่
2. **Categories** (1:N) **Menu_Items** - หมวดหมู่หนึ่งมีเมนูหลายอย่าง
3. **Menu_Items** (N:M) **Ingredients** ผ่าน **Menu_Item_Ingredients** - เมนูหนึ่งใช้วัตถุดิบหลายอย่าง
4. **Users** (1:N) **Orders** - ลูกค้าหนึ่งคนสั่งได้หลายออเดอร์
5. **Orders** (1:N) **Order_Items** - ออเดอร์หนึ่งมีสินค้าหลายชิ้น
6. **Orders** (1:1) **Payments** - ออเดอร์หนึ่งมีการชำระเงินหนึ่งครั้ง
7. **Suppliers** (1:N) **Purchase_Orders** - ผู้จำหน่ายหนึ่งรายมีใบสั่งซื้อหลายใบ
8. **Orders** (1:1) **Deliveries** - ออเดอร์หนึ่งมีการจัดส่งหนึ่งครั้ง
