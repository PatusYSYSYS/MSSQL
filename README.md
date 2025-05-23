📊 Monthly Sales Analysis
This repository contains an SQL query for performing monthly sales analysis based on data from the gold.fact_sales table.

🧠 Purpose of the Query
The query aims to provide a monthly sales summary including:

Total sales amount

Number of unique customers

Total quantity sold

🗃️ Source Table: gold.fact_sales
Description of the columns used in the query:

Column	Type	Description
order_date	DATE	Date when the order was placed
sales_amount	DECIMAL	Value of a single sales transaction
quantity	INT	Number of units sold
customer_key	INT	Unique identifier for the customer

🧾 SQL Query
sql
Kopiuj
Edytuj
SELECT
  MONTH(order_date) as order_month,
  SUM(sales_amount) as total_sales,
  COUNT(DISTINCT customer_key) as total_customers,
  SUM(quantity) as total_quantity
FROM gold.fact_sales
WHERE order_date IS NOT NULL
GROUP BY MONTH(order_date)
ORDER BY MONTH(order_date);
