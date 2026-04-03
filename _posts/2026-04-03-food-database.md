---
title: "My Food Delivery Database in MySQL"
date: 2026-04-03
categories: [Database journey]
tags: [DBS]
layout: post
comments: true
toc: true
image:
  path: https://github.com/user-attachments/assets/7f8bc0bb-4118-440c-9d0a-4b89459af85e
  alt: SQL Database
---

This post is about a comprehensive SQL database schema that is designed to streamline food ordering, restaurant management, and real-time delivery tracking

<!--more-->

# Objective
The objective of this task is to create a database with 10 features and insert 5 records using MySQL Workbench.

# Dataset Description
This dataset represents an online food delivery system where customers order food from different restaurants.

It includes details such as:

- Customer name
- Restaurant name
- Food item
- Price
- Payment method
- Ratings

This dataset helps in understanding how real-world applications like food delivery apps manage data.

## 1️⃣ CREATE DATABASE

```sql
CREATE DATABASE library_db;
USE library_db;
```
## 2️⃣ CREATE TABLES

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_name VARCHAR(50),
    restaurant_name VARCHAR(50),
    food_item VARCHAR(50),
    quantity INT,
    order_price DECIMAL(6,2),
    delivery_city VARCHAR(50),
    order_time VARCHAR(20),
    payment_method VARCHAR(20),
    rating DECIMAL(2,1)
);
```
## 3️⃣ INSERT VALUES

```sql
INSERT INTO orders VALUES
(1, 'Ali', 'Pizza Hut', 'Pepperoni Pizza', 2, 1800.00, 'Lahore', '18:30', 'Cash', 4.5),
(2, 'Sara', 'KFC', 'Zinger Burger', 1, 550.00, 'Faisalabad', '19:00', 'Card', 4.2),
(3, 'Usman', 'McDonalds', 'Big Mac', 2, 1200.00, 'Karachi', '20:15', 'Online', 4.7),
(4, 'Ayesha', 'Dominos', 'Cheese Pizza', 1, 900.00, 'Islamabad', '17:45', 'Cash', 4.3),
(5, 'Hassan', 'Subway', 'Chicken Sandwich', 2, 700.00, 'Multan', '21:00', 'Card', 4.6);
```
## 4️⃣ CHECK TABLE
```sql
SELECT * FROM orders;
```
<img width="819" height="129" alt="imp" src="https://github.com/user-attachments/assets/80791cb4-c8c7-486c-83ce-eaecc7ee2638" />

```sql
SELECT customer_name, order_price 
FROM orders 
WHERE order_price > 1000;
```
<img width="355" height="141" alt="2" src="https://github.com/user-attachments/assets/d73a6906-5f65-4b69-a253-61ee9dd2451f" />

```sql
SELECT * FROM orders WHERE rating > 4.5;
```
<img width="799" height="120" alt="3" src="https://github.com/user-attachments/assets/4f44c8da-d583-4530-80b7-49a0aeb685a6" />
