# Music-Store-Analysis

## Project Overview

**Level**: Intermediate 
## Objective
Analyzed a music store dataset using beginner, intermediate, and advanced SQL techniques to identify high-performing cities based on sales and customer engagement. The goal was to uncover actionable insights to support data-driven business decisions, such as optimizing marketing strategies and store expansion planning.

## Question set 1 - Easy

### 1. Who is the senior most employee based on job title?
```sql
SELECT title, last_name, first_name 
FROM employee
ORDER BY levels DESC
LIMIT 1
```
### 2. Which countries have the most Invoices?
```sql
SELECT COUNT(*) AS c, billing_country 
FROM invoice
GROUP BY billing_country
ORDER BY c DESC
```
### 3. What are top 3 values of total invoice?
```sql
SELECT total 
FROM invoice
ORDER BY total DESC
```
### 4. Which city has the best customers? We would like to throw a promotional Music Festival in the city we made the most money. 
Write a query that returns one city that has the highest sum of invoice totals. 
Return both the city name & sum of all invoice totals 
```sql
SELECT billing_city,SUM(total) AS InvoiceTotal
FROM invoice
GROUP BY billing_city
ORDER BY InvoiceTotal DESC
LIMIT 1;
```
### 5. Who is the best customer? The customer who has spent the most money will be declared the best customer. 
Write a query that returns the person who has spent the most money.
```sql
SELECT customer.customer_id, first_name, last_name, SUM(total) AS total_spending
FROM customer
JOIN invoice ON customer.customer_id = invoice.customer_id
GROUP BY customer.customer_id
ORDER BY total_spending DESC
LIMIT 1;
```

