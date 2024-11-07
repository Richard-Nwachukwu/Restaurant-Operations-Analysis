# Restaurant-Operations-Analysis

## Problem Statement

The Taste of the World Café debuted a new menu at the start of the year. As the data analyst you’ve been asked to dig into the customer data to see which menu items are doing well/ not well and what the top customers seem to like best.

## Objectives

1.	Explore the meu_items table to get an idea of what’s on the new menu
2.	Explore the order_details table to get an idea of the data that’s been collected
3.	Use both tables to understand how customers are reacting to the new menu.

## Case Study questions

OBJECTIVE 1

1. How many Italian dishes are on the menu?

```Sql
SELECT COUNT(*) FROM menu_items
WHERE category = 'Italian';
```
2. What are the least and most expensive Italian dishes on the menu?

```sql
SELECT * FROM menu_items
WHERE category = 'Italian'
ORDER BY price;

SELECT * FROM menu_items
WHERE category = 'Italian'
ORDER BY price DESC;
```

3. How many dishes are in each category?

``` sql
SELECT category, COUNT(item_name) AS num_dishes
FROM menu_items
GROUP BY category;
```

4. Wha is the average dish price within each category?

```sql
SELECT category, AVG(price) AS avg_price FROM menu_items
GROUP BY category;
```

OBJECTIVE 2

5. What is the date range of the table?

```sql
SELECT MIN(order_date), MAX(order_date) 
FROM order_details
;
```

6. How many orders were made within this date range?

```sql
SELECT COUNT(DISTINCT order_id)  AS count_orders
FROM order_details; 
```

7. Which orders had the most number of items?

```sql
SELECT order_id, COUNT(item_id) AS num_items
FROM order_details
GROUP BY order_id
ORDER BY num_items DESC;
```

8. How many orders had more than 12 items?

```sql
SELECT COUNT(*) FROM
(SELECT order_id, COUNT(item_id) AS num_items
FROM order_details
GROUP BY order_id
HAVING num_items >12
) AS num_orders
;
```


















