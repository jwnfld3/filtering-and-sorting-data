# Filtering and Sorting Data

## Overview
This lab introduces basic SQL filtering and sorting techniques using `WHERE`, `ORDER BY`, and logical operators. It builds upon data inserted in SQL Lab 2 and simulates tasks performed by support engineers or analysts filtering records for reports or diagnostics.

## Who / What / Where / When / Why

- **Who**: A reporting analyst tasked with filtering customer orders for a monthly sales report.
- **What**: Use SQL queries to filter and sort data based on specific business rules.
- **Where**: The `ShopEZ` database, using `Customers` and `Orders` tables.
- **When**: After data entry and during reporting or data cleanup.
- **Why**: To extract meaningful subsets of data from larger tables for targeted analysis.

---

## Steps

### Step 1: Switch to the ShopEZ Database

```sql
USE ShopEZ;  -- Sets the context to the ShopEZ database
```

**Explanation**: Ensures all queries target the correct database.

---

### Step 2: Retrieve Orders Over $100

```sql
SELECT * FROM Orders  -- Selects all columns from the Orders table
WHERE TotalAmount > 100;  -- Filters results to only include orders where TotalAmount is greater than 100
```

**Explanation**: Filters the orders to find only high-value transactions.

---

### Step 3: Sort Orders by Most Recent First

```sql
SELECT * FROM Orders  -- Selects all columns from the Orders table
ORDER BY OrderDate DESC;  -- Sorts results in descending order by OrderDate (newest first)
```

**Explanation**: Helps prioritize or review the most recent orders.

---

### Step 4: Filter and Sort Combined

```sql
SELECT * FROM Orders  -- Selects all columns from the Orders table
WHERE TotalAmount > 50  -- Filters to only orders over $50
ORDER BY TotalAmount DESC;  -- Sorts the results by TotalAmount from highest to lowest
```

**Explanation**: Combines filtering and sorting to find larger transactions and ranks them by size.

---

### Step 5: Retrieve Orders by a Specific Customer

```sql
SELECT 
    o.OrderID,
    o.OrderDate,
    o.TotalAmount,
    c.FirstName,
    c.LastName
FROM Orders o  -- Uses alias 'o' for Orders
JOIN Customers c ON o.CustomerID = c.CustomerID  -- Joins Customers to include customer info
WHERE c.FirstName = 'Alice'  -- Filters for records where the customer's first name is Alice
ORDER BY o.OrderDate;  -- Sorts Alice's orders by date (oldest to newest)
```

**Explanation**: Retrieves all orders placed by Alice and displays them in chronological order, useful for customer service reviews or audit trails.

---

## Conclusion
This lab demonstrated how to apply filters and sorting criteria to SQL queries, allowing users to isolate relevant data from large tables. These techniques are essential for operational reporting, quality checks, and business insights.
