# Banking-Transaction-Analysis
 # 🏦 Banking Transaction Analysis (SQL Project)

## 📌 Project Overview

This project implements a **basic banking database system using MySQL**.
It manages customer information and transaction records and demonstrates various SQL operations such as:

* Filtering
* Sorting
* Aggregation
* Joins
* Window Functions
* Subqueries

The purpose of this project is to **practice and demonstrate core SQL concepts** used in real-world database systems.

---

# 🗄️ Database Setup

## Create Database

```sql
CREATE DATABASE bank_system;
USE bank_system;
```

This database stores all tables related to the banking system.

---

# 📋 Tables Used

## 1️⃣ Customers Table

Stores basic information about bank customers.

| Column   | Description                                      |
| -------- | ------------------------------------------------ |
| cus_id   | Unique customer ID (Primary Key, Auto Increment) |
| name     | Customer name                                    |
| email    | Customer email                                   |
| city     | Customer city                                    |
| acc_type | Account type (Savings / Current)                 |
| acc_bal  | Current account balance                          |

**Purpose**

* Maintains customer account details

---

## 2️⃣ Transactions Table

Stores financial transactions performed by customers.

| Column   | Description                                |
| -------- | ------------------------------------------ |
| tra_id   | Unique transaction ID                      |
| cus_id   | Customer ID (Foreign Key)                  |
| amount   | Transaction amount                         |
| tra_type | Type of transaction (credit / debit)       |
| tra_mode | Mode of transaction (UPI, ATM, NEFT, IMPS) |
| tra_date | Date and time of transaction               |

**Purpose**

* Records deposits, withdrawals, and transaction activities

---

# 📥 Sample Data

Customers belong to cities such as:

* Hyderabad
* Delhi
* Mumbai
* Chennai
* Bangalore

Transactions are performed using modes like:

* UPI
* ATM
* NEFT
* IMPS

---

# 🔍 SQL Queries

## 1. View All Customers

```sql
SELECT * FROM customers;
```

## 2. View All Transactions

```sql
SELECT * FROM transactions;
```

## 3. Customers With Balance Greater Than 1500

```sql
SELECT cus_id, name 
FROM customers 
WHERE acc_bal > 1500;
```

## 4. Sort Transactions by Date

```sql
SELECT * 
FROM transactions 
ORDER BY tra_date DESC;
```

## 5. Show Unique Transaction Modes

```sql
SELECT DISTINCT tra_mode 
FROM transactions;
```

## 6. Top 5 Transactions by Amount

```sql
SELECT * 
FROM transactions 
ORDER BY amount DESC 
LIMIT 5;
```

## 7. Customers Whose Name Starts With 'A'

```sql
SELECT * 
FROM customers 
WHERE name LIKE 'A%';
```

## 8. Total Transaction Amount Per Customer

```sql
SELECT cus_id, SUM(amount) 
FROM transactions 
GROUP BY cus_id;
```

## 9. Customers With Total Transactions Greater Than 2000

```sql
SELECT cus_id, SUM(amount)
FROM transactions
GROUP BY cus_id
HAVING SUM(amount) > 2000;
```

## 10. Join Customers and Transactions

```sql
SELECT c.name, t.amount, t.tra_type
FROM customers c
JOIN transactions t 
ON c.cus_id = t.cus_id;
```

## 11. Running Total of Transactions

```sql
SELECT cus_id, amount,
SUM(amount) OVER(
    PARTITION BY cus_id 
    ORDER BY tra_date
) AS running_total
FROM transactions;
```

## 12. Rank Customers by Account Balance

```sql
SELECT name, acc_bal,
DENSE_RANK() OVER(
    ORDER BY acc_bal DESC
) AS rank_no
FROM customers;
```

## 13. Customers With Above-Average Transactions

```sql
SELECT cus_id
FROM transactions
GROUP BY cus_id
HAVING AVG(amount) >
(
    SELECT AVG(amount) 
    FROM transactions
);
```

---

# 🧠 SQL Concepts Demonstrated

* Database Creation
* Table Creation
* Primary Keys
* Foreign Keys
* Data Insertion
* Filtering (WHERE)
* Sorting (ORDER BY)
* Unique Values (DISTINCT)
* Aggregation (SUM, AVG)
* Grouping (GROUP BY)
* Filtering Aggregated Data (HAVING)
* Table Joins
* Window Functions
* Ranking Functions
* Subqueries

---

# ✅ Conclusion

This project simulates a **basic banking system database** and demonstrates how SQL can be used to:

* Manage customer records
* Track transaction activities
* Perform financial analysis
* Generate insights from banking data

It provides a strong foundation for **SQL database design and query optimization**.

