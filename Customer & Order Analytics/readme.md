
# This SQL provides insight into customer and order data.

## Source: Database with 6 tables containing customer data and sales data from January through May.

# 1. How many orders were placed in January? 
SELECT COUNT(orderid)

FROM BIT_DB.JanSales

# 2. How many of those orders were for an iPhone? 
SELECT COUNT(orderid)

FROM BIT_DB.JanSales

WHERE Product='iPhone'

# 3. Select the customer account numbers for all the orders that were placed in February. 
SELECT acctnum

FROM BIT_DB.customers cust

INNER JOIN BIT_DB.FebSales Feb

ON cust.order_id=FEB.orderid

# 4. Which product was the cheapest one sold in January, and what was the price? 
SELECT distinct Product, 

price

FROM BIT_DB.JanSales

WHERE  price in (SELECT min(price) 

FROM BIT_DB.JanSales)

#OR 

SELECT distinct product,

price FROM BIT_DB.JanSales 

ORDER BY price ASC LIMIT 1

# 5. What is the total revenue for each product sold in January?
SELECT sum(quantity)

*price as revenue

,product

FROM BIT_DB.JanSales

GROUP BY product

# 6. Which products were sold in February at 548 Lincoln St, Seattle, WA 98101, how many of each were sold, and what was the total revenue?
select 

sum(Quantity),

product, 

sum(quantity)*price as revenue

FROM BIT_DB.FebSales 

WHERE location = '548 Lincoln St, Seattle, WA 98101'

GROUP BY product

# 7. How many customers ordered more than 2 products at a time, and what was the average amount spent for those customers? 
select 

count(cust.acctnum), 

avg(quantity*price)

FROM BIT_DB.FebSales Feb

LEFT JOIN BIT_DB.customers cust

ON FEB.orderid=cust.order_id

WHERE Feb.Quantity>2

# 8. List all the products sold in Los Angeles in February, and include how many of each were sold.
SELECT 

    Product,
    
    SUM(Quantity) AS total_quantity
    
FROM BIT_DB.FebSales

WHERE location LIKE '%Los Angeles%'
    AND Product <> ''
    AND Product <> 'Product'
    
GROUP BY Product

ORDER BY total_quantity DESC;

# 9 Which locations in New York received at least 3 orders in January, and how many orders did they each receive?
SELECT 

    DISTINCT location,
    
    COUNT(orderID) AS total_orders

    
FROM BIT_DB.JanSales

GROUP BY location

HAVING location LIKE '%NY%'

    AND total_orders >= 3
    
ORDER BY location ASC;

# 10. How many of each type of headphone were sold in February?
SELECT 

    Product,
    
    SUM(Quantity) AS quantity_sold
    
FROM BIT_DB.FebSales

GROUP BY Product

HAVING Product LIKE '%Headphones%'

ORDER BY quantity_sold DESC;

# 11. What was the average amount spent per account in February? (overall average, not average for each account)
SELECT 

    SUM(Quantity * price) / COUNT(customers.acctnum) AS average_amount_spent
    
FROM BIT_DB.FebSales AS feb_sales

LEFT JOIN BIT_DB.customers AS customers

    ON BIT_DB.feb_sales.orderID = BIT_DB.customers.order_ID
    
WHERE orderid <> '' 

AND orderid <> 'Order ID';

# 12. What was the average quantity of products purchased per account in February? (overall average, not average for each account)
SELECT 

    SUM(Quantity) / COUNT(customers.acctnum) AS average_items_purchased
    
FROM BIT_DB.FebSales AS feb_sales

LEFT JOIN BIT_DB.customers AS customers

    ON BIT_DB.feb_sales.orderID = BIT_DB.customers.order_id
    
WHERE orderid <> '' 

AND orderid <> 'Order ID';

# 13. Which product brought in the most revenue in January and how much revenue did it bring in?
SELECT 

    Product,
    
    ROUND(SUM(Quantity * price), 2) AS total_revenue
    
FROM BIT_DB.JanSales

GROUP BY Product

HAVING Product <> ''

    AND Product <> 'Product'
    
ORDER BY total_revenue DESC

LIMIT 1;

# 14. Query the account numbers, count of order IDs, product, quantity, price, order date, and location for all orders that were placed in February.
SELECT 
    c.acctnum,
    
    count(f.orderID) AS orders,
    
    f.product,
    
    f.quantity,
    
    f.price,
    
    f.orderdate,
    
    f.location
    
FROM BIT_DB.FebSales AS f

INNER JOIN BIT_DB.customers AS c

ON f.orderid = c.order_id

GROUP BY 

    c.acctnum,
    
    f.product,
    
    f.quantity,
    
    f.price,
    
    f.orderdate,
    
    f.location;


