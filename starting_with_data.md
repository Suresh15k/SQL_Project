Question 1: find the orders not in stock from the sales table 

SQL Queries:

SELECT * FROM products 
WHERE "orderedQuantity" > "stockLevel"products table 

Answer: 15 SKU orderd is not in stock 



Question 2: What is the major source visitor 

SQL Queries:
SELECT DISTINCT "channelGrouping", COUNT (*) FROM allsessions 
GROUP BY DISTINCT "channelGrouping"
ORDER BY count (*) DESC

Answer: Most of the visitors are through Organic, Direct & Refferal



Question 3: which Day of the week most visit happend 

SQL Queries:

SELECT   Count ("visitId"), TO_CHAR ( date, 'DAY' ) AS Day
FROM analytics
GROUP BY Day
ORDER BY Count ("visitId") DESC

Answer: Most of the visit happend during tuesday and suprisingly weekend contains least visits 



Question 4: What are the top 5 visited product names 

SQL Queries:
SELECT  Count ("visitId"), "v2ProductName"
FROM allsessions
GROUP BY "v2ProductName"
ORDER BY Count ("visitId") DESC limit 5

Answer:
295	"Google Men's 100% Cotton Short Sleeve Hero Tee White"
245	"22 oz YouTube Bottle Infuser"
221	"YouTube Twill Cap"
211	"YouTube Custom Decals"
197	"YouTube Men's Short Sleeve Hero Tee Black"



Question 5: Which Channel grouping created most revenue 

SQL Queries:
SELECT "channelGrouping", SUM ("transactionRevenue")
FROM allsessions
GROUP BY "channelGrouping"
ORDER BY SUM ("transactionRevenue") 

Answer: vistis via Referral generated high revenue 
