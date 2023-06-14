What issues will you address by cleaning the data?
large transaction country 

select country, city, sum("totalTransactionRevenue") from allsessions
group by city, country
order by sum("totalTransactionRevenue") desc


DATA CLEANING 

# Reducing the unit price value by dividing 
UPDATE analytics 
SET unit_price = unit_price / 1000000; 

# Added Primary Key to the analytics table 

ALTER TABLE analytics 
ADD COLUMN id SERIAL PRIMARY KEY;

# Deleting the duplicate rows 

Delete from analytics a 
USING analytics b 
WHERE 
a.id > b.id
AND a."visitId" = b."visitId"

# Deleted Id and made VisitID as PK

ALTER TABLE analytics 
DROP COLUMN id :
ADD PRIMARY KEY ("visitId")

# Converted Date column from integer to date type 

ALTER TABLE analytics 
ALTER COLUMN date  TYPE DATE 
using date :: Text :: DATE;

# Droped Redendunt Column UserID in analytics 

ALTER Table analytics 
DROP COLUMN userid ;

# Replacing Null Values in Allsessions with Zero 

UPDATE allsessions 
SET "totalTransactionRevenue"  = 0
WHERE "totalTransactionRevenue" is null




Queries:
Below, provide the SQL queries you used to clean your data.
