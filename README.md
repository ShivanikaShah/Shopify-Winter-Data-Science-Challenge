# Shopify-Winter-Data-Science-Challenge
https://jobs.smartrecruiters.com/Shopify/743999796500238-data-science-intern-summer-2022-remote-us-canada-


Summer 2022 Data Science Intern Challenge
# Question 1: 
Given some sample data, write a program to answer the following: click here to access the required data set

On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 


a.	Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 

The wrong calculation is because we considered count instead of sum for our dataset.

Also, as each of the 100 shops sell different models, the average value might not give the correct results as it doesn’t take the frequency of the values. A weighted average or median maybe a better metric for this data which is also robust to any outliers. 

We can calculate a column as AOV = order_amount/total_items and analyse it further to find the trend for 30 days for different models. We can also see that there are some outliers (extreme values of 25725 as AOV), we can’t remove it from our data but we need to treat it separately after further analysis.

b.	What metric would you report for this dataset?

I would consider Median a better metric here giving weightage to all the models AOV and being robust to outliers.

c.	What is its value?
The Median of calculated AOV is 153.

# Question 2: 
For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.


a.	How many orders were shipped by Speedy Express in total?

Select Count(OrderID) FROM Orders, Shippers Where Orders.ShipperID = Shippers.ShipperID and ShipperName = "Speedy Express"

Ans: 54

b.	What is the last name of the employee with the most orders?

SELECT [Employees].LastName, COUNT (*) AS NOrders
FROM [Orders]
JOIN [Employees]
ON [Orders].EmployeeID = [Employees].EmployeeID
GROUP BY [Employees].LastName
ORDER BY NOrders DESC

Ans: Peacock – 40

c.	What product was ordered the most by customers in Germany?
SELECT Products.ProductName FROM Orders INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID INNER JOIN OrderDetails ON Orders.OrderID = OrderDetails.OrderID INNER JOIN Products ON OrderDetails.ProductID = Products.ProductID WHERE Customers.Country = 'Germany' GROUP BY Products.ProductName ORDER BY COUNT(Products.ProductName) DESC

Ans: Gorgonzola Telino 

