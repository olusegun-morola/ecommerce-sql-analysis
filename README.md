# E-commerce SQL Practice

## Project Overview

I created an e-commerce database called **`e_commerce`** and created the following tables:

* `customer`
* `orders`
* `order_items`
* `products`
* `reviews`

This project contains SQL queries I used to practice filtering, aggregation, grouping, sorting, limiting results, and joining tables.

---

## Query 1 — Filtering Products

### SQL Query

```sql
SELECT *
FROM products
WHERE unit_price >= 20
LIMIT 10;
```

### Explanation

I used this query to select products with a **unit price of 20 or more**.

The `LIMIT 10` clause restricts the result to **10 records**.

---

## Query 2 — Counting Distinct Products

### SQL Query

```sql
SELECT COUNT(DISTINCT product_name)
FROM products;
```

### Explanation

I used `COUNT(DISTINCT product_name)` to count the **unique product names** in the `products` table.

Using `DISTINCT` means that duplicate product names are counted only once.

---

## Query 3 — Grouping, Aggregating and Sorting Products

### SQL Query

```sql
SELECT
    product_name,
    SUM(unit_price) AS total_price
FROM products
GROUP BY product_name
HAVING SUM(unit_price) >= 20
ORDER BY SUM(unit_price) DESC
LIMIT 10;
```

### Explanation

I used `SUM(unit_price)` to calculate the total unit price for each product name and renamed the result as `total_price`.

I then used `GROUP BY product_name` to group the records by product name.

The `HAVING` clause keeps only product groups where the total unit price is **20 or more**.

Finally, I used `ORDER BY ... DESC` to sort the results from the **highest total price to the lowest**, and `LIMIT 10` to display the top 10 results.

---

## Query 4 — Finding the Highest Product Price

### SQL Query

```sql
SELECT MAX(unit_price) AS highest_price
FROM products;
```

### Explanation

I used the `MAX()` function to find the **highest unit price** in the `products` table.

I renamed the result as `highest_price`.

---

## Query 5 — Joining Products and Reviews

### SQL Query

```sql
SELECT
    products.product_id,
    product_name,
    category,
    reviews.rating,
    review_text
FROM products
INNER JOIN reviews
    ON products.product_id = reviews.product_id
ORDER BY product_name DESC;
```

### Explanation

I used an `INNER JOIN` to combine information from the `products` and `reviews` tables using `product_id` as the matching column.

The query returns the product ID, product name, category, review rating, and review text.

I then used `ORDER BY product_name DESC` to sort the product names in **descending alphabetical order (Z to A)**.
## Author

**Olusegun Morola**

Aspiring Data Analyst | Excel | SQL | Power BI
