# Intro_to_DB

A simple MySQL introduction project that explores basic database operations — from creating databases and tables to inserting and viewing data — using SQL and Python.

##  Project Overview

This project, **alx_book_store**, is a beginner-friendly database setup for an online bookstore.  
It demonstrates how to:

- Create a database
- Define and relate tables
- Insert and view data
- Automate database creation with Python

---

##  Database Schema

**Database name:** `alx_book_store`

### Tables
1. **Authors**
   - `author_id` (Primary Key)
   - `author_name` VARCHAR(215)

2. **Books**
   - `book_id` (Primary Key)
   - `title` VARCHAR(130)
   - `author_id` (Foreign Key → Authors)
   - `price` DOUBLE
   - `publication_date` DATE

3. **Customers**
   - `customer_id` (Primary Key)
   - `customer_name` VARCHAR(215)
   - `email` VARCHAR(215)
   - `address` TEXT

4. **Orders**
   - `order_id` (Primary Key)
   - `customer_id` (Foreign Key → Customers)
   - `order_date` DATE

5. **Order_Details**
   - `orderdetailid` (Primary Key)
   - `order_id` (Foreign Key → Orders)
   - `book_id` (Foreign Key → Books)
   - `quantity` DOUBLE

---

##  Files Description

| File Name | Description |
|------------|-------------|
| `MySQLServer.py` | Python script that connects to MySQL and creates the database `alx_book_store`. |
| `alx_book_store.sql` | SQL file that defines all tables and their relationships. |
| `task_2.sql` | Creates all five tables in the `alx_book_store` database. |
| `task_3.sql` | Lists all tables in the database. |
| `task_4.sql` | Displays a full description of the `Books` table using `INFORMATION_SCHEMA`. |
| `task_5.sql` | Inserts a single row into the `customer` table. |
| `task_6.sql` | Inserts multiple rows into the `customer` table. |

---

##  How to Run

### 1. Create the Database
```bash
python3 MySQLServer.py

---

##  Create Tables
mysql -u root -p alx_book_store < task_2.sql

---

##  List Tables
mysql -u root -p alx_book_store < task_3.sql

---

##  Describe Books Table
mysql -u root -p alx_book_store < task_4.sql

---

##  Insert Single Customer
mysql -u root -p alx_book_store < task_5.sql

---

##  Insert Multiple Customers
mysql -u root -p alx_book_store < task_6.sql

---

##  Database Relationship Diagram (ASCII)

Below is a visual representation of the relationships between the tables:

+-------------+ +-----------+ +-----------+ +----------------+
| Authors | | Books | | Orders | | Order_Details |
|-------------| |-----------| |-----------| |----------------|
| author_id PK|<--+----| book_id PK| | order_id PK|<--+---| orderdetailid PK|
| author_name | | | title | | customer_id| | | order_id FK |
+-------------+ | | author_id FK-------+------------+ | | book_id FK------+
| | price | | | quantity |
| | publication_date | | +----------------+
| +-----------+ |
| |
| |
| +-------------+ |
+----| Customers |----------------------+
|-------------|
| customer_id PK|
| customer_name |
| email |
| address |
+---------------+


**Legend:**
- `PK` → Primary Key  
- `FK` → Foreign Key  
- Lines represent relationships between tables

---

##  Sample SQL Queries to Explore the Database
1️⃣ View All Books
SELECT * FROM books;

2️⃣ View All Customers
SELECT * FROM customers;

3️⃣ View Books with Their Authors
SELECT b.title, a.author_name, b.price
FROM books b
JOIN authors a ON b.author_id = a.author_id;

4️⃣ View Orders with Customer Names
SELECT o.order_id, c.customer_name, o.order_date
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;

5️⃣ View Full Order Details (Books, Customers, Quantity)
SELECT c.customer_name, b.title, od.quantity, o.order_date
FROM order_details od
JOIN orders o ON od.order_id = o.order_id
JOIN books b ON od.book_id = b.book_id
JOIN customers c ON o.customer_id = c.customer_id;

6️⃣ Count of Books Per Author
SELECT a.author_name, COUNT(b.book_id) AS total_books
FROM authors a
LEFT JOIN books b ON a.author_id = b.author_id
GROUP BY a.author_name;

---

## Setup Troubleshooting Guide
🔹 1. MySQL Connection Error
Error: mysql.connector.errors.InterfaceError: 2003: Can't connect to MySQL server on 'localhost' (10061)

 Fix:
-Make sure your MySQL service is running.
-Restart MySQL:
sudo service mysql restart
-Double-check your credentials (username/password).

🔹 2. Access Denied Error
Error: mysql.connector.errors.ProgrammingError: 1045 (28000): Access denied for user

Fix:
-Verify your MySQL username and password.
-Try logging in manually:
mysql -u root -p
-If you’re using a different user, grant privileges:
GRANT ALL PRIVILEGES ON *.* TO 'your_user'@'localhost' IDENTIFIED BY 'your_password';
FLUSH PRIVILEGES;

🔹 3. Missing MySQL Connector Module
Error: ModuleNotFoundError: No module named 'mysql'

 Fix:
-Install the connector:
pip install mysql-connector-python

🔹 4. Database Already Exists
If you rerun MySQLServer.py and see:
mysql.connector.errors.DatabaseError: 1007 (HY000): Can't create database; database exists

 Fix:
The script is already designed to skip if the database exists.
You can also safely ignore this message — it just means your database is already created.

🔹 5. SQL Syntax Error
Error Example:
ERROR 1064 (42000): You have an error in your SQL syntax

 Fix:
-Ensure all SQL keywords are in UPPERCASE.
-End each SQL statement with a semicolon ;.
-Check for typos in table or column names.

---
##  Made by thevirtualtechmaven — Full Stack Web Developer
