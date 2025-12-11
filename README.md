# Azure Projects

### 📝 Project Summary
This repository contains exercises completed as part of the Azure Fundamentals module of the Data Technician bootcamp. It showcases hands-on practice with SQL, non-relational databases and Azure Data Factory. The exercises cover a variety of skills relevant to data analysis, data engineering and cloud-based data workflows.

The project includes:
- SQL exercises using Azure SQL.
- Exploration of non-relational database concepts.
- End-to-end ETL workflow exercises (using Azure Data Factory)

Screenshots, outputs and example SQL queries are included in my [Data Technician bootcamp workbook](files/Data-Technician-Workbook-ADF.pdf).


---
### 🖌️ Skills Practiced
- writing SQL queries including joins, filtering and aggregate functions.
- Using Azure SQL for querying relational databases.
- Understanding non-relational databases (NoSQL).
- Designing ETL workflows and practicing data transformation.

---
### 🔎 Example SQL Queries
Below are some exmaples of SQL queries performed using the AdventureWorks sample database in an Azure lab on SKillable. 

**1. Total Quantity Sold per Product**
``` sql
SELECT ProductID, Name, ListPrice FROM [SalesLT].[Product]
WHERE ListPrice>(SELECT AVG(ListPrice)
FROM [SalesLT].[Product])
ORDER BY ListPrice DESC; 
```

**2. Products Priced Above List Price** 
```sql
SELECT [SalesLT].[SalesOrderDetail].ProductID, Name, sum(OrderQty) AS Total_Quantity_Sold
FROM [SalesLT].[SalesOrderDetail]
INNER JOIN [SalesLT].[Product] ON [SalesLT].[SalesOrderDetail].ProductID=[SalesLT].[Product].ProductID
GROUP BY [SalesLT].[SalesOrderDetail].ProductID,Name
ORDER BY Total_Quantity_Sold DESC; 
```

**3. Products with Highest Profit Margin**
```sql
SELECT TOP 1 Name, ListPrice, StandardCost, (ListPrice - StandardCost) AS Profit
FROM [SalesLT].[Product]
ORDER BY Profit DESC; 
```

**4. Difference Between Average Standard Cost and Average List Price**
```sql
SELECT [SalesLT].[SalesOrderHeader].SalesOrderId, OrderDate, [SalesLT].[Customer].CustomerID, FirstName, LastName, TotalDue, Status, ProductID, OrderQty
FROM [SalesLT].[SalesOrderHeader]
INNER JOIN [SalesLT].[Customer] ON [SalesLT].[SalesOrderHeader].CustomerID=[SalesLT].[Customer].CustomerID
INNER JOIN [SalesLT].[SalesOrderDetail] ON [SalesLT].[SalesOrderHeader].SalesOrderID=[SalesLT].[SalesOrderDetail].SalesOrderID; 
```

**5. Number of Products per Category**
```sql
SELECT [SalesLT].[ProductCategory].Name, COUNT(*) AS Product_Count
FROM [SalesLT].[ProductCategory]
INNER JOIN [SalesLT].[Product] ON [SalesLT].[ProductCategory].ProductCategoryID=[SalesLT].[Product].ProductCategoryID
GROUP BY [SalesLT].[ProductCategory].Name; 
```
#### NoSQL and Data Factory
Completed exercises using Azure Cosmos DB, a cloud-based NoSQL database and practiced end-to end data integration in Data Factory. These exercises, including screenshots, are showcased in my [Data Technician bootcamp workbook](files/Data-Technician-Workbook-ADF.pdf).

---
### 🪞Reflections
- Gained confience writing queries using the AdventureWorks database, reinforcing my understand of relational data manipulation.
- Learned how to design end-to-end data integration pipelines, including extracting, transforming and loading data.
- Developed familaroty with Azure Cosmos DB and understand of scenarios where non-relational databases are advantageous.
