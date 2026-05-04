Cafe Sales Analysis

# Project Overview
This project forcasts sales of a Cafe. It showcases information of how the cafe is performing in different cities, which products are the best and how much sales are being generated. 

# Tools Used
- Excel
- BigQuery
- Tableau
- GitHub

## Key Insights
- Sales peaked around mid-February. Sales started to fall end of March.
- Sydney CBD had the highest sales.
- Sandwiches generated the highest profit.
- Card payments were the most common payment method.
- Wait time had little impact on customer ratings.

## Dashboard
![Dashboard](Tableau%20Dashboard.png)


## SQL Queries

View full dataset:

SELECT * FROM `project-1b5d408f-99f4-4c24-a09.beginner_projects.cafe`;

 Highest sales by store location:
 
SELECT store_location, SUM(sales)
FROM `project-1b5d408f-99f4-4c24-a09.beginner_projects.cafe`
group by store_location;

 Most profitable product categories:
 
select product_category, SUM(profit)
FROM `project-1b5d408f-99f4-4c24-a09.beginner_projects.cafe`
group by product_category;

Busiest days based on sales:

select day_name, SUM(sales)
FROM `project-1b5d408f-99f4-4c24-a09.beginner_projects.cafe`
group by day_name;

Impact of wait time on customer ratings:

SELECT
  CASE
    WHEN wait_time < 5 THEN 'Short Wait'
    WHEN wait_time BETWEEN 5 AND 15 THEN 'Medium Wait'
    ELSE 'Long Wait'
  END AS wait_category,
  
  AVG(customer_rating) AS avg_rating,
  COUNT(*) AS total_orders

FROM `project-1b5d408f-99f4-4c24-a09.beginner_projects.cafe`
GROUP BY wait_category
ORDER BY avg_rating DESC;

Most used payment methods:

select COUNT(payment_method)
FROM `project-1b5d408f-99f4-4c24-a09.beginner_projects.cafe`
group by payment_method;

Sales trend over time (daily):

SELECT
  order_date,
  SUM(sales) AS total_sales
FROM `project-1b5d408f-99f4-4c24-a09.beginner_projects.cafe`
GROUP BY order_date
ORDER BY order_date;
