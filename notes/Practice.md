![](images/DBImage.png)
##### Join Multi Table
```sql
select ProductName, OrderDate, CustomerName
from Orders O, OrderDetails OD, Products P, Customers C
Where O.OrderID = OD.OrderID and P.ProductsID = OD.ProductID and C.customerID = O.CustomerID
```
The SQL query retrieves a list of product names, order dates, and customer names by joining four tables: `Orders`, `OrderDetails`, `Products`, and `Customers`. It uses the following conditions to link the tables:
1. **Orders** and **OrderDetails** are joined on `OrderID`.
2. **OrderDetails** and **Products** are joined on `ProductID`.
3. **Orders** and **Customers** are joined on `CustomerID`.
The result provides a combined view of each order, including the product details and the customer who placed the order. This query is useful for analyzing customer purchases and order history.

```sql
select ProductName, OrderDate, CustomerName
from Orders O inner join OrderDetails OD
	on O.OrderID = OD.OrderID
	inner join products P
	on P.ProductID = OD.ProductID
	inner join Customers C
	on C.customerID = O.CustomerID
```

This SQL query is a more modern and explicit version of the previous query, it retrieves **product names**, **order dates**, and **customer names** by explicitly joining four tables: `Orders`, `OrderDetails`, `Products`, and `Customers`. It uses **INNER JOIN** to combine the tables based on the following relationships:
1. **Orders** and **OrderDetails** are joined on `OrderID`.
2. **OrderDetails** and **Products** are joined on `ProductID`.
3. **Orders** and **Customers** are joined on `CustomerID`.
The result provides a clear view of each order, including the product details and the customer who placed it. This query is more readable and modern compared to the previous version, using explicit `INNER JOIN` syntax. It is useful for analyzing customer purchases and generating order-related reports.

##### Join with DML
```sql
UPDATE C
SET city = 'London'
FROM Customers C INNER JOIN Orders O 
ON C.customerID = O.CustomerID
WHERE C.city = 'Cairo';
```
1. **UPDATE C**: Updates the `Customers` table (aliased as `C`).
2. **SET city = 'Cairo'**: Changes the `city` to `'Cairo'` for matching rows.
3. **FROM Customers C**: Specifies the `Customers` table as the source for the update.
4. **INNER JOIN Orders O**: Joins the `Customers` table with the `Orders` table to ensure only customers with orders are updated.
5. **WHERE C.city = 'London'**: Filters the update to apply only to customers whose current city is `'London'`.
