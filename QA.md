What are your risk areas? Identify and describe them.
The aim of the quality assurance process is to make sure the data is relevent. The process removes duplicate values and errors like worng data types and incomplete values. The risk of using uncleaned data is quite high. Unformated data leads to wrong analysis with misleading insigts and the decisions arrived using the results will lead to high risk of loosing the business. 

Following are some of the queries used to do QA checks 
QA Process:

# Check for Null/Missing Values in Column 
SELECT * FROM analytics 
WHERE "visitId" is Null 

Result - No Rows appeared 

# QA for checking duplicates 

SELECT "productSKU", Count (total_ordered) As order_count FROM sales_SKU
GROUP BY "productSKU"
HAVING  Count (total_ordered) > 1

Results - No Rows appeared

# Check for relevent catogeries in large database 

SELECT DISTINCT "channelGrouping" FROM allsessions 

Result - Small Quantity of Other catogeries listed 

# Check for unrealistic values 

SELECT * FROM sales_report
WHERE ratio > 1

Couple of row has value more than 1 

