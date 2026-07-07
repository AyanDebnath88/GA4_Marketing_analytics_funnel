

# Data Model

---

# Overview

This project simulates an end-to-end Google Analytics 4 (GA4) implementation for an e-commerce SaaS business.

The data model combines:

- Google Analytics 4
- Google Ads
- Meta Ads
- Ecommerce Transactions

The objective is to build a complete Marketing Analytics solution using Python, SQL and Power BI.

---

# Entity Relationship Diagram

```
Users
   │
   │ 1:M
   ▼
Sessions
   │
   │ 1:M
   ▼
Events
   │
   ├──────────────┐
   ▼              ▼
Purchases      Products

Google Ads
      │
      ▼
Campaign Performance

Meta Ads
      │
      ▼
Campaign Performance
```

---

# Table 1 — Users

Primary Key

user_id

Description

Contains one record for every unique website visitor.

| Column | Data Type | Description |
|----------|------------|----------------|
| user_id | VARCHAR | Unique User ID |
| first_visit_date | DATE | First website visit |
| country | VARCHAR | User Country |
| city | VARCHAR | User City |
| device | VARCHAR | Mobile/Desktop/Tablet |
| browser | VARCHAR | Chrome, Safari, Firefox |
| language | VARCHAR | Browser Language |
| age_group | VARCHAR | Simulated demographic |

Estimated Rows

25,000

---

# Table 2 — Sessions

Primary Key

session_id

Foreign Key

user_id

Description

Each website visit creates one session.

| Column | Data Type | Description |
|----------|------------|----------------|
| session_id | VARCHAR | Session Identifier |
| user_id | VARCHAR | FK -> Users |
| session_start | DATETIME | Session Start Time |
| session_duration | INTEGER | Seconds |
| source | VARCHAR | Google, Direct, Facebook |
| medium | VARCHAR | Organic, CPC, Email |
| campaign | VARCHAR | Marketing Campaign |
| landing_page | VARCHAR | Entry Page |
| engaged_session | BOOLEAN | Engaged Session |

Estimated Rows

80,000

---

# Table 3 — Events

Primary Key

event_id

Foreign Key

session_id

Description

Stores every GA4 event.

| Column | Data Type | Description |
|----------|------------|----------------|
| event_id | VARCHAR | Event Identifier |
| session_id | VARCHAR | FK -> Sessions |
| event_name | VARCHAR | GA4 Event |
| event_timestamp | DATETIME | Timestamp |
| page_title | VARCHAR | Page Name |
| page_location | VARCHAR | URL |
| event_value | FLOAT | Optional Value |

Possible Events

- session_start
- page_view
- scroll
- click
- search
- login
- sign_up
- view_item
- add_to_cart
- begin_checkout
- add_payment_info
- purchase

Estimated Rows

500,000+

---

# Table 4 — Products

Primary Key

product_id

Description

Master product catalog.

| Column | Data Type | Description |
|----------|------------|----------------|
| product_id | VARCHAR | Product ID |
| product_name | VARCHAR | Product Name |
| category | VARCHAR | Category |
| brand | VARCHAR | Brand |
| price | DECIMAL | Product Price |

Estimated Rows

500

---

# Table 5 — Purchases

Primary Key

transaction_id

Foreign Keys

user_id

product_id

Description

Completed ecommerce purchases.

| Column | Data Type | Description |
|----------|------------|----------------|
| transaction_id | VARCHAR | Transaction ID |
| user_id | VARCHAR | FK -> Users |
| product_id | VARCHAR | FK -> Products |
| purchase_date | DATETIME | Purchase Time |
| quantity | INTEGER | Units |
| revenue | DECIMAL | Revenue |
| payment_method | VARCHAR | Card, UPI, Wallet |
| coupon | VARCHAR | Coupon Used |

Estimated Rows

12,000

---

# Table 6 — Google Ads

Primary Key

campaign_id

Description

Google Ads campaign performance.

| Column | Data Type | Description |
|----------|------------|----------------|
| campaign_id | VARCHAR | Campaign ID |
| campaign_name | VARCHAR | Campaign Name |
| impressions | INTEGER | Impressions |
| clicks | INTEGER | Clicks |
| cost | DECIMAL | Ad Spend |
| conversions | INTEGER | Conversions |

Estimated Rows

300

---

# Table 7 — Meta Ads

Primary Key

campaign_id

Description

Meta Ads performance.

| Column | Data Type | Description |
|----------|------------|----------------|
| campaign_id | VARCHAR | Campaign ID |
| campaign_name | VARCHAR | Campaign Name |
| impressions | INTEGER | Impressions |
| clicks | INTEGER | Clicks |
| spend | DECIMAL | Ad Spend |
| purchases | INTEGER | Purchases |

Estimated Rows

300

---

# Relationships

Users (1)
↓

Sessions (Many)

Sessions (1)
↓

Events (Many)

Users (1)
↓

Purchases (Many)

Products (1)
↓

Purchases (Many)

Google Ads
↓

Campaign Dashboard

Meta Ads
↓

Campaign Dashboard

---

# Business KPIs

Traffic

- Users
- Sessions
- New Users
- Returning Users
- Engagement Rate

Marketing

- CTR
- CPC
- CPM
- CPA
- CAC
- ROAS

Sales

- Revenue
- Orders
- Conversion Rate
- Average Order Value

Customer

- Lifetime Value
- Repeat Purchase Rate
- Revenue per User

Product

- Top Products
- Category Revenue
- Units Sold

---

# Technologies

- Google Analytics 4
- Python
- SQL
- Power BI
- Git
- GitHub
