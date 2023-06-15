Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:
SELECT country, city, SUM ("totalTransactionRevenue") FROM allsessions 
GROUP BY country, city 
ORDER BY SUM ("totalTransactionRevenue") DESC ;

Answer:
Higest total revenue by country is US & Canada & with states its "San Francisco" and "Sunnyvale" 


**Question 2: What is the average number of products ordered from visitors in each city and country?**

SQL Queries:
SELECT al.city, al.country, a."fullvisitorId", AVG (a.units_sold) 
FROM allsessions as al 
JOIN analytics as a USING ("visitId")
GROUP BY al.city, al.country, a."fullvisitorId"
ORDER BY AVG (a.units_sold) DESC

Answer:
Average is 1 for Singapore & Canada 



**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:
SELECT  al.country, al.city, al."v2ProductCategory", COUNT (al."v2ProductCategory")
OVER (PARTITION BY  al.country ORDER BY al.city)
FROM allsessions as al 
JOIN analytics as a USING ("visitId")
where "productQuantity" > '0'



Answer: Most of the states in US has orderd the same categoery of products 





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:
select subquery.country, subquery."v2ProductName", subquery.product_revenue, ROW_NUMBER() OVER (PARTITION BY subquery.country order by subquery.product_revenue DESC) as top_selling from
(SELECT  al.country, al."v2ProductName", SUM (al."totalTransactionRevenue") as product_revenue 
FROM allsessions as al 
JOIN analytics as a USING ("visitId")
WHERE al."totalTransactionRevenue" > 0
GROUP BY al.country, al."v2ProductName"
ORDER BY al.country, product_revenue DESC) subquery
WHERE top_selling = 1 


Answer: Top Selling product in Swizerland is "YouTube Men's 3/4 Sleeve Henley" and in US is "Nest® Learning Thermostat 3rd Gen-USA - Stainless Steel"





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:

SELECT  al.country, al.city, SUM (al."totalTransactionRevenue") as product_revenue
FROM allsessions as al 
WHERE al."totalTransactionRevenue" > 0
GROUP BY al.country, al.city 
ORDER BY product_revenue DESC ;


Answer: Visitors from US city has contributed most 







