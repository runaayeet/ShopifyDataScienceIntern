# ShopifyDataScienceIntern

#Winter 2021 Data Science Intern Challenge 
#Please complete the following questions, and provide your thought process/work. You can attach your work in a text file, link, etc. on the application page. Please ensure answers are easily visible for reviewers!


#Question 1: Given some sample data, write a program to answer the following: click here to access the required data set
#On Shopify, we have exactly 100 sneaker shops, and each of these shops sells only one model of shoe. We want to do some analysis of the average order value (AOV). When we look at orders data over a 30 day window, we naively calculate an AOV of $3145.13. Given that we know these shops are selling sneakers, a relatively affordable item, something seems wrong with our analysis. 
#1. Think about what could be going wrong with our calculation. Think about a better way to evaluate this data. 

###ANSWER: The average is not an accurate way to display the data needed to understand on average how much each order is across the 100 sneaker shops over 30 days. The number has been skewed due to outliers in the dataset such as order id 16 and order id 61. In order to mitigate this issue, a better way to evaluate the data would be to use alternative metrics such as median values for order totals. 
          ###In addition the data could be analyzed and reported clearer. For example, the average or median order for each sneaker shop over a 30 day window since they only sell one model of shoe. 

#Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.
#1. How many orders were shipped by Speedy Express in total?

###ANSWER:
SELECT Shippers.ShipperName,COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
GROUP BY ShipperName;
###54 orders were shipped by Speedy Express in Total 

#2. What is the last name of the employee with the most orders?
###ANSWER:
SELECT Employees.LastName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
LEFT JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
GROUP BY LastName;
###Peacock was the last name of the employee with the most orders

#3. What product was ordered the most by customers in Germany?
###ANSWER: 
SELECT       `ProductID`, Country,
             COUNT(`ProductID`) AS `most_ordered`
    FROM     `OrderDetails`, Customers
    WHERE Country='Germany'
    GROUP BY `ProductID`
    ORDER BY most_ordered DESC;
